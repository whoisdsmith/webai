```
<<<<<<< HEAD
[project-name]/
=======
ephemera-codex/
>>>>>>> 9f5128ed64282129518a1d3fbf1a5defd1b6ebf5
├── .github/
│   └── copilot-instructions.md - Custom instructions for GitHub Copilot.
├── .gitignore - Files and folders to be ignored by Git.
├── architectural-notes.md - Key architectural decisions and notes.
├── functional-requirements.md - Detailed functional requirements.
├── fileNames.md - This file! Map of project file structure.
├── gemini/
│   ├── gemini_system_prompt.md - System prompt for Gemini.
│   └── [feature_name]_prompt.md - Example feature-specific prompt for Gemini.
├── package.json - Project dependencies and scripts.
├── public/
│   └── index.html - Main HTML file.
├── README.md - Project overview and development guide.
├── src/
│   ├── App.js - Main application component.
│   ├── components/
│   │   ├── [Component1Name]/
│   │   │   ├── index.js - Main file for Component 1.
│   │   │   └── [Component1Name].module.css - Component 1 specific styles.
│   │   ├── [Component2Name].js - Component 2.
│   │   └── ...
│   ├── index.js - Entry point for the React application.
│   ├── styles.css - Global styles.
│   └── utils/
<<<<<<< HEAD
│       ├── [utility1].js - Utility function 1.
│       └── ...
=======
│       ├── bootSequence.js - Defines the sequence of boot messages and logic for determining message types (normal, warning, error).
│       ├── constants.js -  Holds constant values used throughout the application (e.g., colors, timing delays, error messages).
│       ├── logger.js - Provides logging functionality for debugging and simulating system logs. It might wrap `console.log`, `console.warn`, and `console.error`.
│       └── timing.js - Contains utility functions related to timing and delays, such as the delay between boot messages.
>>>>>>> 9f5128ed64282129518a1d3fbf1a5defd1b6ebf5
└── ...
```