# Creating utility methods with React Testing Library

[React Testing Library](https://testing-library.com/docs/react-testing-library/intro) encourages developers to write tests that resemble how users use an application, by providing a light-weight API to query the DOM instead of React components.

As we write tests, we look for elements and perform actions:

```js
const searchInput = screen.getByRole('textbox', { name: /search/i });
const submitButton = screen.getByRole('button', { name: /submit/i });

userEvent.type(searchInput, 'keywords');
userEvent.click(submitButton);
```

As we write more tests, we repeat queries and actions:

```js
import React from 'react'
import { render, screen, waitFor } from '@testing-library/react'
import userEvent from '@testing-library/user-event'
import '@testing-library/jest-dom/extend-expect'

describe('MyComponent', () => {
  it('renders a search input', () => {
    render(<MyComponent />);

    const searchInput = screen.getByRole('textbox', { name: /search/i });
    expect(searchInput).toBeInTheDocument();
  });

  it('renders a submit button', () => {
    render(<MyComponent />);

    const submitButton = screen.getByRole('button', { name: /submit/i });
    expect(submitButton).toBeInTheDocument();
  });

  it('initially disables the submit button', () => {
    render(<MyComponent />);

    const submitButton = screen.getByRole('button', { name: /submit/i });
    expect(submitButton).toBeDisabled();
  });

  it('enables the submit button after entering a search query', () => {
    render(<MyComponent />);

    const searchInput = screen.getByRole('textbox', { name: /search/i });
    userEvent.type(searchInput, 'keywords');

    const submitButton = screen.getByRole('button', { name: /submit/i });
    expect(submitButton).toBeEnabled();
  });

  it('searches for results', () => {
    render(<MyComponent />);

    const searchInput = screen.getByRole('textbox', { name: /search/i });
    userEvent.type(searchInput, 'keywords');

    const submitButton = screen.getByRole('button', { name: /submit/i });
    userEvent.click(submitButton);

    await waitFor(() => {
      const searchResults = screen.getByRole('heading', { name: /search results/i });
      expect(searchResults).toBeInTheDocument();
    });
  });
});
```

With all of this code duplication, we can see that most of our tests would fail if we changed any labels. These tests are brittle.

So, we can do better. We can create utility methods:

```js
const getSearchInput = () => screen.getByRole('textbox', { name: /search/i });
const getSubmitButton = () => screen.getByRole('button', { name: /submit/i });

const typeSearchQuery = (searchQuery = 'keywords' ) => {
  userEvent.type(getSearchInput(), searchQuery);
};
```

Then, we can create a custom `render` methods that provides these utilities:

```js
import React from 'react'
import { render as rtlRender, screen, waitFor } from '@testing-library/react'
import userEvent from '@testing-library/user-event'
import '@testing-library/jest-dom/extend-expect'

const render = ui => {
  rtlRender(ui);

  const getSearchInput = () => screen.getByRole('textbox', { name: /search/i });
  const getSubmitButton = () => screen.getByRole('button', { name: /submit/i });

  const typeSearchQuery = (searchQuery = 'keywords' ) => {
    userEvent.type(getSearchInput(), searchQuery);
  };

  return {
    getSearchInput,
    getSubmitButton,
    typeSearchQuery,
  };
};
```

Finally, let's put it all together to simplify our tests:


```js
import React from 'react'
import { render as rtlRender, screen, waitFor } from '@testing-library/react'
import userEvent from '@testing-library/user-event'
import '@testing-library/jest-dom/extend-expect'

describe('MyComponent', () => {
  const render = ui => {
    rtlRender(ui);

    const getSearchInput = () => screen.getByRole('textbox', { name: /search/i });
    const getSubmitButton = () => screen.getByRole('button', { name: /submit/i });

    const typeSearchQuery = (searchQuery = 'keywords' ) => {
      userEvent.type(getSearchInput(), searchQuery);
    };

    return {
      getSearchInput,
      getSubmitButton,
      typeSearchQuery,
    };
  };

  it('renders a search input', () => {
    const { getSearchInput } = render(<MyComponent />);

    expect(getSearchInput()).toBeInTheDocument();
  });

  it('renders a submit button', () => {
    const { getSubmitButton } = render(<MyComponent />);

    expect(getSubmitButton()).toBeInTheDocument();
  });

  it('initially disables the submit button', () => {
    const { getSubmitButton } = render(<MyComponent />);

    expect(submitButton).toBeDisabled();
  });

  it('enables the submit button after entering a search query', () => {
    const { getSubmitButton, typeSearchQuery } = render(<MyComponent />);

    typeSearchQuery();

    expect(getSubmitButton()).toBeEnabled();
  });

  it('searches for results', () => {
    const { getSubmitButton } = render(<MyComponent />);

    typeSearchQuery();
    userEvent.click(getSubmitButton());

    await waitFor(() => {
      const searchResults = screen.getByRole('heading', { name: /search results/i });
      expect(searchResults).toBeInTheDocument();
    });
  });
});
```
