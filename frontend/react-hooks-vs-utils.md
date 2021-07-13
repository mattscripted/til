# React Hooks vs Utilities

Often, we need to reuse logic across features. In React, we can either use hooks or utility functions.

## React Hooks

React hooks ["let you use state and other React features without writing a class"](https://reactjs.org/docs/hooks-intro.html).

```js
import React, { useState } from 'react';

const useToggle = (initialState) => {
  const [state, setState] = useState(initialState);

  const toggleState = () => setState(!state);

  return [state, toggleState];
};

const Component = () => {
  const [isVisible, toggleIsVisible] = useToggle(true);

  return (
    <>
      <button onClick={() => toggleIsVisible()}>
        Toggle content
      </button>
      {isVisible && (
        <div>
          This content is visible.
        </div>
      )}
    </>
  );
};
```

If you need access to React features, such as `useState` or `useEffect`, then use a hook. However, hooks are limited to React.

## Utility Functions

Utility functions ["[accomplish] routine programming tasks"](https://www.quora.com/What-is-a-utility-method). They are helper methods for anything at all -- such as calling APIs, modifying variables, or tracking events.

```js
import React from 'react';

// Track an event through Segment's API
const track = (eventName, eventProps = {}) => {
  analytics.track(eventName, eventProps)
}

const Component = () => (
  <button onClick={() => track('Button Clicked')}>
    Track click
  </button>
);

window.addEventListener('DOMContentLoaded', () => {
  track('Page Loaded');
});
```

If you don't need access to React features, and don't expect to need access to React features, then use a utility function. This way, you can reuse your logic anywhere.
