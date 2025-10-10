# Signaling When Datastar Has Loaded for Third-Party Libraries

#patterns #integrations #getting-started

> **Version**: Applicable for Datastar v1.0.0-RC.5

## Overview

Third-party libraries or custom scripts sometimes need to know when Datastar has fully initialized before they can safely interact with Datastar-managed elements or signals. This guide shows how to dispatch a custom event when Datastar is ready.

## Implementation

Use the `data-on-load` attribute to dispatch a custom event when Datastar loads an element into the DOM:

```html
<div data-on-load="document.dispatchEvent(new CustomEvent('datastar-loaded', {bubbles: true}))"></div>
```

Place this element in your HTML where you want to signal Datastar's initialization (typically near the top of your `<body>` or after including the Datastar script).

## How It Works

### Attribute Explained

**`data-on-load`**
- A Datastar event attribute that triggers when an element is loaded into the DOM
- Executes during initial page load for elements present in the HTML
- Also fires when elements are dynamically patched into the DOM via SSE updates
- Provides a reliable hook for initialization code

### Flow

1. **Element Load**: When Datastar processes the element with `data-on-load`, it executes the expression
2. **Custom Event**: `document.dispatchEvent(new CustomEvent('datastar-loaded', {bubbles: true}))` creates and dispatches a custom event that bubbles up through the DOM
3. **Third-party integration**: External scripts can listen for this event to know when Datastar is ready

## Listening for the Event

Third-party libraries or scripts can listen for the event:

```javascript
document.addEventListener('datastar-loaded', () => {
  console.log('Datastar is now loaded and ready');
  // Initialize third-party library that depends on Datastar
  initMyLibrary();
});
```

To handle cases where the script loads after Datastar:

```javascript
let datastarReady = false;

document.addEventListener('datastar-loaded', () => {
  datastarReady = true;
  initMyLibrary();
});

// Fallback: check if we missed the event
setTimeout(() => {
  if (!datastarReady && document.querySelector('[data-on-load]')) {
    // Datastar likely already loaded
    initMyLibrary();
  }
}, 100);
```

## Use Cases

1. **Analytics Integration**: Initialize analytics that track Datastar signal changes
2. **UI Component Libraries**: Bootstrap components that interact with Datastar's reactive system
3. **Polyfills/Feature Detection**: Execute code that needs to run after Datastar initializes
4. **Web Components**: Signal custom elements that they can safely interact with Datastar
5. **Development Tools**: Initialize debugging or development utilities that monitor Datastar

## Notes

- The event fires when the element with `data-on-load` is loaded into the DOM
- For most use cases, placing this near the top of your `<body>` provides the earliest notification
- If Datastar fragments are loaded dynamically, the event will fire each time that specific element is patched into the DOM
- Consider using a more specific event name (e.g., `myapp-datastar-ready`) if you need to avoid conflicts

## Alternative Approaches

- Place your initialization code in a `<script>` tag after the element with `data-on-load`
- Use `data-on-load` directly on elements that need initialization:
  ```html
  <div data-on-load="initMyComponent(el)"></div>
  ```
