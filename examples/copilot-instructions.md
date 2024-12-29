# GitHub Copilot Custom Instructions: The Ephemera Codex

This file provides custom instructions for GitHub Copilot to tailor its assistance to the specific needs and constraints of "The Ephemera Codex" project.

## Project-Specific Context

"The Ephemera Codex" is an interactive website that presents a fictional narrative intertwined with technical elements. The story revolves around a character named Greg Reeves and his creations:

*   **GregOS:** A simulated operating system that reflects Greg's emotional and psychological state. It has a retro, terminal-like aesthetic.
*   **Project Amoratus:** An advanced, fictional technology involving a neural interface and a mysterious material called "QuantumMind."

The website aims to create an immersive experience, using interactive elements, visual effects (like glitches), and a fragmented narrative style to explore themes of memory, trauma, consciousness, and the ethics of technology.

## Coding Style and Conventions

*   **Language:**  We are using JavaScript with React.
*   **Framework:** React (using Create React App or Vite setup).
*   **Component Style:** Use **React functional components** with **hooks** for state management and side effects.
*   **Styling:** **Tailwind CSS** is used for styling. Apply Tailwind classes using the `className` attribute.
*   **State Management:** We are using the **React Context API with `useReducer`** for managing global state.
*   **Formatting:**
    *   Use **2 spaces** for indentation.
    *   Use single quotes for strings unless escaping is needed.
    *   Add a space after keywords (e.g., `if (...)`, `for (...)`, `while (...)`).
    *   Add a space before and after operators (e.g., `a + b`, `c === d`).
*   **Naming Conventions:**
    *   **Components:** `PascalCase` (e.g., `GregOSBootScreen`, `NavigationMenu`, `QuantumMindDiagram`)
    *   **Files:** `camelCase` (e.g., `gregOSBootScreen.js`, `navigationMenu.js`, `quantumMindDiagram.js`)
    *   **Variables and Functions:** `camelCase` (e.g., `bootSequence`, `handleClick`, `userPreferences`)
    *   **CSS Classes:**  Use `BEM` (Block, Element, Modifier) in conjunction with Tailwind's utility classes (e.g., `gregos-boot-screen__message`, `navigation-menu__item--active`)
*   **Comments:** Add comments to explain complex logic, algorithms, or any code that might not be immediately obvious.
*   **Error Handling:** Use `console.log` (for general information), `console.warn` (for warnings), and `console.error` (for errors) for logging, especially to simulate system messages in GregOS.
*   **Accessibility:** Adhere to WCAG guidelines. Use semantic HTML elements and ARIA attributes when necessary. Ensure sufficient color contrast and keyboard navigability.

## Development Environment Constraints

*   We are using **Bolt.new**, a web-based development environment that uses a **WebContainer**.
*   **IMPORTANT:**  Bolt's WebContainer **cannot run native binaries**.
*   **IMPORTANT:** There is **NO `pip`** or any Python package manager other than the standard library available. Do not attempt to install Python packages.
*   **IMPORTANT:** There is **NO `g++` or C/C++ compiler**. Do not attempt to compile C/C++ code.
*   **IMPORTANT:**  **Git is NOT available** within the Bolt environment.
*   **IMPORTANT:** Use only the limited set of available shell commands: cat, chmod, cp, echo, hostname, kill, ln, ls, mkdir, mv, ps, pwd, rm, rmdir, xxd, alias, cd, clear, curl, env, false, getconf, head, sort, tail, touch, true, uptime, which, code, jq, loadenv, node, python3, wasm, xdg-open, command, exit, export, source.
*   **Data Storage:** We are not using an external database. Any persistent data will be stored using the browser's `localStorage` or will be managed within the application's state.

## Test Generation Instructions

*   **Framework:** Use **React Testing Library** and **Jest** for writing tests.
*   **Focus:** Prioritize testing component behavior, interactions, and state updates.
*   **Coverage:** Aim for high test coverage of components and utility functions.
*   **Test Files:** Place test files alongside the components they are testing, using the naming convention `[ComponentName].test.js` (e.g., `GregOSBootScreen.test.js`).

## Code Review Instructions

*   **Accessibility:** Pay close attention to accessibility. Ensure that the website is usable by people with disabilities, adhering to WCAG guidelines.
*   **Coding Style:** Verify that the code adheres to the project's coding style and conventions (defined above).
*   **Performance:** Look for potential performance bottlenecks, especially in animations, data rendering, and state updates. Optimize where necessary.
*   **Error Handling:** Check that errors are handled gracefully and that appropriate feedback is provided to the user.
*   **Security:** While this is a mostly client-side application, be mindful of any potential security vulnerabilities, especially when dealing with user input or sensitive data.
*   **Maintainability:** Ensure the code is well-structured, modular, and easy to understand.

## Commit Message Instructions

*   **Format:** Use the imperative mood in the subject line (e.g., "Fix: Resolve boot sequence error").
*   **Subject Line Length:** Keep the subject line under 50 characters.
*   **Body:** Provide a more detailed explanation in the commit message body, if necessary. Explain the *why* behind the change, not just the *what*.
*   **References:**  Reference related issues or components using keywords like "Fixes #1" (if you're using GitHub issues) or "Relates to INT3RN4L_3RR0R_ST0RY."

## Specific to The Ephemera Codex

*   When generating code related to **GregOS**, simulate a retro, terminal-like aesthetic. Use monospace fonts (like VT323), and a color scheme with bright greens, blues, or reds on a black background.
*   For **Project Amoratus** components, use a more futuristic and abstract visual style.
*   Remember that **"INT3RN4L_3RR0R_ST0RY"** is the core narrative component. When generating code for it, consider the fragmented and emotional nature of the story.
*   Use **glitch effects** sparingly and intentionally, primarily within the "INT3RN4L_3RR0R_ST0RY" section or to reflect system instability in GregOS.
*   When generating code for error messages or system logs, follow the format: `INT3RN4L_3RR0R: [Error Description]` or `WARNING: [Warning Description]`.
*   The **Ethical Considerations Matrix** should present information in a clear, structured way, allowing for easy navigation and linking to relevant content.

## Examples

Here are a few examples of how you might phrase instructions for specific scenarios within the context of this project:

*   "When creating components for Project Amoratus, prioritize visual representations of data and technology over realistic depictions."
*   "For the GregOS boot sequence, simulate occasional errors with messages like 'INT3RN4L_3RR0R: Memory corruption detected.' or 'WARNING: Emotional core instability detected.'"
*   "When working on the 'INT3RN4L_3RR0R_ST0RY' section, use the 'glitch' CSS class to create a visual glitch effect where appropriate to reflect Greg's fragmented memories."
*   "In the `Dashboard` component, ensure that each navigation button has a clear `onClick` handler that updates the `currentPage` state in the `App` component."

These instructions will be automatically added to the context that Copilot uses to assist you in the Bolt editor, helping it generate more relevant and helpful suggestions.