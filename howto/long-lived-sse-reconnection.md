# How-to for a long-lived datastar stream that tries to reconnect forever

#real-time #patterns

> **Attribution:** This guide was originally created by [@gazpachoking](https://github.com/gazpachoking)
> Source: https://gist.github.com/gazpachoking/d45df5f89e481a2cb675122eb7e9e359

## Intro

Datastar automatically retries SSE connections in many cases, but does not retry in situations that typically signal the end of a stream, such as error responses or graceful server disconnects.

## Goal

Persist an SSE connection through server restarts and temporary error responses, and notify the user about connection status.

## Steps

The solution uses two key Datastar attributes:
- `data-on-interval`: Repeatedly attempt to connect to the server
- `data-indicator`: Set a signal while connecting or connected

Example code:

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
