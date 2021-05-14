# redux-mock-store supports getting state with a function

[redux-mock-store](https://github.com/reduxjs/redux-mock-store) is great for testing actions. However, it does not support reducers, so your [state will never update](https://github.com/reduxjs/redux-mock-store/issues/71).

When you want to test more complex logic, which relies on changing state, you can simulate reducers with a `getState` function.

```js
import configureStore from 'redux-mock-store';

const middlewares = [];
const mockStore = configureStore(middlewares);

describe('some function or component', () => {
  it('gets state from a function', () => {
    const initialState = { ... };
    const reducer = (state, action) => {
      // Mock your reducer function
      // Or better yet, use your real reducer
    };
    const getState = actions => actions.reduce(reducer, initialState);
    const store = mockStore(getState);

    expect(store.getState()).toEqual(initialState);

    const action = { ... };
    store.dispatch(action);

    const expectedStateAfterAction = { ... };
    expect(store.getState()).toEqual(expectedStateAfterAction);
  });
});
```
