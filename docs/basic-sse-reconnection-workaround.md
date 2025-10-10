# Basic SSE Reconnection Workaround

#real-time #patterns #workaround

> **Version**: Applicable for Datastar v1.0.0-RC.5
>
> **⚠️ Note**: This is a basic workaround approach and not a comprehensive solution.
>
> **Attribution:** This guide was originally created by [@gazpachoking](https://github.com/gazpachoking)
> Source: https://gist.github.com/gazpachoking/d45df5f89e481a2cb675122eb7e9e359

## Intro

Datastar automatically retries SSE connections in many cases, but does not retry in situations that typically signal the end of a stream, such as error responses or graceful server disconnects. This workaround provides a simple polling mechanism to maintain connections.

## Goal

Persist an SSE connection through server restarts and temporary error responses, and notify the user about connection status.

## Steps

The solution uses several key Datastar attributes working together:

### Attributes Explained

**`data-indicator="_connecting"`**
- Creates a signal `$_connecting` that tracks the fetch request status
- Automatically set to `true` when a request starts, `false` when it completes
- Used to prevent multiple simultaneous connection attempts

**`data-on-interval__duration.30s.leading`**
- Triggers an event every 30 seconds
- `.leading` modifier: fires immediately on page load, then every 30s
- Expression `!$_connecting && @get('/updates')`: only attempts connection if not currently connecting

**`data-signals-_disconnected="false"`**
- Initializes the `$_disconnected` signal to `false`
- Used to track connection status for user notifications

**`data-on-datastar-fetch`**
- Listens to fetch lifecycle events from Datastar
- Updates `$_disconnected` based on connection state:
  - Sets to `false` when receiving SSE events (successful connection)
  - Sets to `true` on 'retrying', 'error', or 'finished' events

**`data-show="$_disconnected"`**
- Shows/hides the warning message based on connection status
- Only visible when `$_disconnected` is `true`

### Example code:

```html
<div data-indicator="_connecting"
     data-on-interval__duration.30s.leading="!$_connecting && @get('/updates')">
</div>

<div data-signals-_disconnected="false"
     data-indicator="_connecting"
     data-on-interval__duration.30s.leading="!$_connecting && @get('/updates')"
     data-on-datastar-fetch="el === evt.detail.el &&
                           ((evt.detail.type.startsWith('datastar') && ($_disconnected = false)) ||
                           (['retrying', 'error', 'finished'].includes(evt.detail.type) && ($_disconnected = true)))">
</div>
<div data-show="$_disconnected">Warning: Not connected to server.</div>
```

## Conclusion

The default Datastar retry semantics are usually best, but this approach allows retrying even through clear connection termination indicators.
