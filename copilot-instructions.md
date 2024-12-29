# GitHub Copilot Custom Instructions: [Project Name]

```
This file provides custom instructions for GitHub Copilot to tailor its assistance to the specific needs and constraints of the [Project Name] project.

## Project-Specific Context

[Provide a brief overview of the project, its goals, and any unique aspects that Copilot should be aware of. For example:]

"[Project Name] is a web application that [brief description]. It aims to create [type of experience] for users by [mentioning key features or interactions]. The project explores themes of [list themes] and uses a [describe visual style] aesthetic."

## Coding Style and Conventions

*   **Language:** [e.g., JavaScript, TypeScript]
*   **Framework:** [e.g., React, Vue, Angular]
*   **Component Style:** [e.g., React functional components with hooks]
*   **Styling:** [e.g., Tailwind CSS, CSS Modules, Styled Components]
*   **State Management:** [e.g., Context API, Redux, Vuex]
*   **Formatting:**
    *   [Indentation: e.g., 2 spaces, 4 spaces, tabs]
    *   [Quotes: e.g., single quotes, double quotes]
    *   [Spacing: e.g., spaces around operators, after keywords]
*   **Naming Conventions:**
    *   **Components:** [e.g., PascalCase]
    *   **Files:** [e.g., camelCase, kebab-case]
    *   **Variables and Functions:** [e.g., camelCase]
    *   **CSS Classes:** [e.g., BEM, kebab-case]
*   **Comments:** [When to add comments, what to include in comments]
*   **Error Handling:** [How to handle errors, logging practices]
*   **Accessibility:** [Specific accessibility requirements, e.g., WCAG guidelines, use of ARIA attributes]

## Development Environment Constraints

*   We are using **Bolt.new**, a web-based development environment that uses a **WebContainer**.
*   **IMPORTANT:** Bolt's WebContainer **cannot run native binaries**.
*   **IMPORTANT:** There is **NO `pip`** or any Python package manager other than the standard library available. Do not attempt to install Python packages.
*   **IMPORTANT:** There is **NO `g++` or C/C++ compiler**. Do not attempt to compile C/C++ code.
*   **IMPORTANT:** **Git is NOT available** within the Bolt environment.
*   **IMPORTANT:** Use only the limited set of available shell commands: cat, chmod, cp, echo, hostname, kill, ln, ls, mkdir, mv, ps, pwd, rm, rmdir, xxd, alias, cd, clear, curl, env, false, getconf, head, sort, tail, touch, true, uptime, which, code, jq, loadenv, node, python3, wasm, xdg-open, command, exit, export, source
*   **Data Storage:** [How data is stored, e.g., local storage, no external database]

## Test Generation Instructions

*   **Framework:** [e.g., Jest, React Testing Library, Mocha]
*   **Focus:** [What to prioritize when writing tests, e.g., component behavior, interactions, edge cases]
*   **Coverage:** [Target test coverage percentage or specific areas to cover]
*   **Test Files:** [Naming conventions for test files, where to place them]

## Code Review Instructions

*   **Accessibility:** [What to look for in terms of accessibility]
*   **Coding Style:** [How to ensure adherence to the project's coding style]
*   **Performance:** [What to look for in terms of performance optimizations]
*   **Error Handling:** [How to ensure proper error handling]
*   **Security:** [Any specific security considerations for the project]
*   **Maintainability:** [How to ensure the code is maintainable and easy to understand]

## Commit Message Instructions

*   **Format:** [e.g., imperative mood, subject line length]
*   **Subject Line Length:** [e.g., under 50 characters]
*   **Body:** [What to include in the commit message body]
*   **References:** [How to reference issues or other relevant information]

## Specific to [Your Project]

[Add any instructions that are specific to your project's unique features, components, or themes. For example:]

*   "When generating code for [specific component], make sure to follow the [specific pattern or style]."
*   "If the generated code involves [specific theme or concept], ensure that it aligns with the overall narrative and aesthetic of the project."
*   "Use the `[custom-class]` CSS class to apply [specific visual effect] in the [specific section] of the website."

## Examples

[Provide a few examples of how you might phrase instructions or comments within your code to guide Copilot effectively. This helps Copilot understand the type of code you expect it to generate.]
```
**Example 1: Generating a new React component:**

```javascript
// src/components/MyNewComponent.js
import React from 'react';

// Create a functional component called MyNewComponent that takes a 'title' prop
// and renders it in an h1 tag with Tailwind CSS classes for styling.
// Add a button that, when clicked, logs "Button clicked!" to the console.
const MyNewComponent = ({ title }) => {
  // Your code here, and Copilot will assist based on the comment above
};

export default MyNewComponent;
```

**Example 2: Implementing a specific function:**

```javascript
// src/utils/dataUtils.js

/**
 * This function takes an array of numbers and returns the average.
 * It should handle empty arrays by returning 0.
 * Use reduce to calculate the sum.
 */
export const calculateAverage = (numbers) => {
  // Your code here, Copilot will use the JSDoc comment for guidance
};
```

**Example 3: Adding a CSS animation in Tailwind:**

```javascript
// src/components/AnimatedComponent.js
import React from 'react';

// Create a component with a div that has a subtle pulse animation
// using Tailwind CSS.
const AnimatedComponent = () => {
  return (
    <div className="animate-pulse bg-blue-500 p-4 rounded">
      This is an animated component.
    </div>
  );
};

export default AnimatedComponent;
```

**Example 4: Using `localStorage` for data persistence:**

```javascript
// src/utils/storageUtils.js

// Create a function to save user preferences to localStorage.
// The function should take a 'preferences' object as an argument.
export const saveUserPreferences = (preferences) => {
  // Your code here
};

// Create a function to load user preferences from localStorage.
// It should return an empty object if no preferences are found.
export const loadUserPreferences = () => {
  // Your code here
};
```

**Example 5: Implementing State Management with Context API and useReducer:**

```javascript
// src/context/AppContext.js
import React, { createContext, useReducer } from 'react';

// Create an AppContext using createContext.
export const AppContext = createContext();

// Define the initial state for the app.
const initialState = {
  count: 0,
};

// Create a reducer function that handles 'INCREMENT' and 'DECREMENT' actions.
const appReducer = (state, action) => {
  // Your code here
};

// Create an AppProvider component that uses useReducer and provides the state and dispatch to its children.
export const AppProvider = ({ children }) => {
  const [state, dispatch] = useReducer(appReducer, initialState);

  return (
    <AppContext.Provider value={{ state, dispatch }}>
      {children}
    </AppContext.Provider>
  );
};
```

**Example 6: Writing a test with React Testing Library:**

```javascript
// src/components/MyComponent.test.js
import React from 'react';
import { render, screen, fireEvent } from '@testing-library/react';
import MyComponent from './MyComponent';

// Test that MyComponent renders correctly.
test('renders MyComponent with title', () => {
  render(<MyComponent title="Test Title" />);
  const titleElement = screen.getByText(/Test Title/i);
  expect(titleElement).toBeInTheDocument();
});

// Test that the button click in MyComponent logs to the console.
test('button click logs to console', () => {
  const consoleSpy = jest.spyOn(console, 'log');
  render(<MyComponent title="Test Title" />);
  const buttonElement = screen.getByRole('button');
  fireEvent.click(buttonElement);
  expect(consoleSpy).toHaveBeenCalledWith('Button clicked!');
  consoleSpy.mockRestore();
});
```
