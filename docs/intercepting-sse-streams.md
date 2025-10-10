# Intercepting and Modifying SSE Streams

#real-time #patterns #advanced

> **Version**: Applicable for Datastar v1.0.0-RC.5
>
> **Attribution:** [@alvarolm](https://github.com/alvarolm)

## Overview

While Datastar doesn't provide built-in hooks for intercepting Server-Sent Events (SSE) streams, you can use fetch monkey-patching to intercept and transform responses before Datastar processes them. This technique allows you to modify SSE data, add logging, implement caching, or apply custom transformations.

## Implementation

This approach works by replacing the native `fetch` function with a custom wrapper that intercepts responses and optionally transforms their body streams:

```javascript
// Store reference to original fetch
const originalFetch = window.fetch;

// Replace window.fetch with custom implementation
window.fetch = async function (url, options = {}) {
  try {
    // Call original fetch
    const response = await originalFetch(url, options);

    // If no body, return original response
    if (!response.body) {
      return response;
    }

    // Call transformer to get TransformStream (or null if no transform needed)
    const transformStream = fetchStreamTransformer({
      url,
      options,
      response,
    });

    // If transformer returns null, no transformation needed
    if (!transformStream) {
      return response;
    }

    // Create new response with transformed body
    // IMPORTANT: This is compatible with Datastar's fetch handling because:
    // 1. For SSE streams: Datastar uses response.body directly
    //    - Our transformed stream works perfectly with getBytes(response.body)
    // 2. For HTML/JSON: Datastar calls response.text()
    //    - Response.text() works on our transformed ReadableStream
    // 3. Response object properly exposes the transformed body through both
    //    response.body (as ReadableStream) and response.text() (as Promise<string>)
    const transformedBody = response.body.pipeThrough(transformStream);

    return new Response(transformedBody, {
      status: response.status,
      statusText: response.statusText,
      headers: response.headers,
    });
  } catch (error) {
    // If transformation fails, log error and re-throw
    console.error('Fetch interception error:', error);
    throw error;
  }
};
```

## How It Works with Datastar

Datastar handles different response types through the Response API:
- **SSE Streams**: Datastar reads from `response.body` using `getBytes()`
- **HTML/JSON**: Datastar calls `response.text()` to get the content

The transformed ReadableStream works with both approaches because the Response API properly exposes the transformed body through both `response.body` and `response.text()`.

## Example Transform Stream

Here's an example transformer that logs SSE events and optionally modifies them:

```javascript
function fetchStreamTransformer({ url, response }) {
  // Only transform SSE streams
  const contentType = response.headers.get('content-type') || '';
  if (!contentType.includes('text/event-stream')) {
    return null;
  }

  const textDecoder = new TextDecoder();
  const textEncoder = new TextEncoder();

  return new TransformStream({
    transform(chunk, controller) {
      try {
        // Decode the chunk
        const text = textDecoder.decode(chunk, { stream: true });

        // Log the SSE event
        console.log(`[SSE from ${url}]:`, text);

        // Optional: Modify the chunk
        // const modified = text.replace(/some-pattern/g, 'replacement');
        // controller.enqueue(textEncoder.encode(modified));

        // Pass through unchanged
        controller.enqueue(chunk);
      } catch (error) {
        console.error('Transform stream error:', error);
        // Pass through original chunk on error
        controller.enqueue(chunk);
      }
    },
    flush(controller) {
      // Clean up any remaining data on stream end
      try {
        const final = textDecoder.decode();
        if (final) {
          console.log(`[SSE final from ${url}]:`, final);
        }
      } catch (error) {
        console.error('Transform stream flush error:', error);
      }
    }
  });
}
```

## Error Handling

The code examples include error handling at multiple levels:

1. **Fetch-level errors**: The try/catch in the fetch wrapper catches errors during response interception and transformation setup
2. **Transform-level errors**: The try/catch in the transform function handles errors during chunk processing
3. **Flush errors**: The flush function handles errors when cleaning up remaining data

**Best Practices:**
- Always wrap transform logic in try/catch to prevent stream errors from breaking the connection
- Pass through the original chunk if transformation fails to maintain data flow
- Log errors for debugging but avoid throwing errors that would terminate the stream
- Use the `flush` callback to handle any buffered data when the stream ends

## Use Cases

1. **Debugging**: Log all SSE events to understand data flow
2. **Analytics**: Track SSE connection lifecycle and data volumes
3. **Caching**: Store and replay SSE streams for offline support
4. **Data Transformation**: Modify SSE payloads before Datastar processes them
5. **Error Recovery**: Intercept and recover from malformed SSE data
6. **Security**: Filter or sanitize SSE content

## Important Notes

- This technique monkey-patches the global `fetch` function and affects all fetch calls
- Apply the patch before Datastar initializes to ensure it intercepts all requests
- Consider performance implications when transforming large streams
- This approach is not officially supported by Datastar and may require updates if Datastar's internals change

## Alternative Approaches

For simpler use cases, consider:
- Server-side transformations before sending SSE events
- Custom event handlers on the client after Datastar processes events
- Datastar plugins if official plugin support becomes available
