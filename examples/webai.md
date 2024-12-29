## WebAI: A Guide to Developing Websites with AI Assistants

**Phase 1: Project Planning and Documentation**

This phase focuses on creating the foundational documents that will guide both you and the AI assistants throughout the development process.

**Step 1: Project Outline (`project-outline.md` - Optional but Recommended)**

*   **Purpose:**  A high-level overview of your website project. This helps you solidify your ideas and provides a starting point for more detailed planning.
*   **Content:**
    *   **Project Name:**  (e.g., "The Ephemera Codex")
    *   **Project Description:** A brief summary of the website's purpose, target audience, and key features.
    *   **Goals:** What do you want to achieve with this website?
    *   **Scope:** What features are essential for the initial release (MVP - Minimum Viable Product)? What can be added later?
    *   **Inspiration:** Links to websites or designs that inspire you.
    *   **Initial Thoughts:** Any initial ideas about the design, functionality, or technology stack.

**Step 2: Functional Requirements Document (`functional-requirements.md`)**

*   **Purpose:**  A detailed document that outlines *what* the website should do, focusing on its features and functionalities from a user's perspective.
*   **Content:**
    *   **Introduction:** Briefly describe the purpose and scope of the document.
    *   **User Classes and Characteristics:** Define the different types of users who will interact with the website.
    *   **Operating Environment:** Specify the target platforms (e.g., web browsers, mobile devices).
    *   **Design and Implementation Constraints:**  Note any limitations or requirements related to technology, development environment, or design.
    *   **Specific Requirements:**  This is the core of the document. Break down each feature into specific, testable requirements. Use a consistent format for each requirement:
        *   **ID:** A unique identifier (e.g., `NAV-001`, `AUTH-002`).
        *   **Feature:** A brief description of the feature (e.g., "User Registration," "Navigation Menu").
        *   **Description:** A more detailed explanation of the feature's functionality.
        *   **Priority:** (e.g., Must Have, Should Have, Could Have, Won't Have). This helps prioritize development.
        *   **Input:** What input does the feature require from the user or system?
        *   **Processing:** What steps or logic are involved in the feature's functionality?
        *   **Output:** What is the result of the feature's execution (e.g., display a message, update data, navigate to a new page)?
    *   **Non-Functional Requirements:** (e.g., performance, security, accessibility, usability).
    *   **Future Enhancements:** (Optional) List features that are out of scope for the initial release but might be considered later.
    *   **Glossary:** Define any project-specific terms or acronyms.

**Step 3: Architectural Notes (`architectural-notes.md`)**

*   **Purpose:** Documents the technical decisions, design patterns, and overall structure of the website. This is essential for guiding Gemini and Copilot in generating code that aligns with your intended architecture.
*   **Content:**
    *   **Overview:** A brief summary of the website's architecture.
    *   **Technology Stack:**
        *   **Frontend Framework:** (e.g., React, Vue.js, Svelte)
        *   **Styling:** (e.g., CSS Modules, styled-components, Tailwind CSS)
        *   **State Management:** (if needed) (e.g., Redux, Vuex, Context API)
        *   **Data Fetching:** (e.g., `fetch`, `axios`)
        *   **Testing:** (e.g., Jest, React Testing Library)
        *   **Other Libraries:** Any other significant libraries or tools you plan to use.
    *   **Development Environment:** (e.g., Bolt, local development setup)
    *   **Design Patterns:** Describe any specific design patterns you'll be using (e.g., component-based architecture, model-view-controller).
    *   **Component Structure:**  Outline the main components of your website and their relationships.
    *   **Coding Conventions:** Define coding style guidelines (e.g., naming conventions, code formatting, commenting style).
    *   **Error Handling:** Describe your approach to handling errors.
    *   **Accessibility:** Outline your strategy for ensuring accessibility.
    *   **AI Assistants Integration:**  Explain how you intend to use Gemini and Copilot in the development process.
    *   **Specific Considerations:** Any project-specific notes or constraints.

**Step 4: File Structure Map (`fileNames.md`)**

*   **Purpose:**  Provides a clear, hierarchical representation of your project's file and folder structure. This helps Gemini understand the organization of your codebase.
*   **Content:**
    *   **Hierarchical Structure:** Use indentation or Markdown list syntax to show the folder structure.
    *   **File Names and Descriptions:** List all files (and folders) with concise descriptions of their purpose.
    *   **Example:**

```markdown
project-root/
├── public/
│   └── index.html - Main HTML file.
├── src/
│   ├── components/
│   │   ├── Header.js - Website header component.
│   │   ├── Footer.js - Website footer component.
│   │   └── HomePage.js - Component for the home page.
│   ├── App.js - Main application component.
│   └── styles.css - Global styles for the website.
├── package.json - Project dependencies and scripts.
└── README.md - Project documentation.
```

**Phase 2: AI Assistant Configuration**

This phase focuses on setting up the files that will directly instruct and provide context to Gemini and Copilot.

**Step 5: Gemini System Prompt (`gemini/gemini_system_prompt.md`)**

*   **Purpose:**  This file contains the initial prompt you'll use to "brief" Gemini about your project. It sets the stage for your entire interaction with Gemini.
*   **Content:**
    *   **Role Definition:** Clearly define Gemini's role (e.g., "You are an experienced software architect...").
    *   **Project Description:** Provide a concise summary of your project.
    *   **Project File Structure:**  Paste the content of your `fileNames.md` file (or a link to it if it's hosted online).
    *   **Core Functionality Overview:** Briefly summarize the key features and functionalities from your `functional-requirements.md`.
    *   **Key Architectural Notes:**  Include the most important points from your `architectural-notes.md`, especially regarding technology choices, design patterns, and coding conventions.
    *   **Tech Stack:**  List the main technologies you're using.
    *   **Development Environment:**  Specify that you're using Bolt and highlight any relevant constraints (WebContainer limitations).
    *   **Instructions for Gemini:**  Clearly instruct Gemini on how you want it to assist you. For example:
        *   "When analyzing issues, consider the project structure, architectural decisions, and best practices for maintainable code."
        *   "Focus on providing clear explanations, identifying relevant files, and suggesting efficient approaches that GitHub Copilot can help implement."
        *   "Adhere to the constraints of the Bolt.new development environment."

**Step 6: Copilot Custom Instructions (`.github/copilot-instructions.md`)**

*   **Purpose:** Provides specific instructions to GitHub Copilot to guide its code generation, testing, code review, and commit message generation.
*   **Content:**
    *   **Project-Specific Context:**  Briefly describe your project and its unique elements.
    *   **Coding Style and Conventions:**
        *   Formatting (e.g., indentation, spacing)
        *   Naming conventions (e.g., `camelCase` for variables, `PascalCase` for components)
        *   Preferred libraries or approaches (e.g., "Use React functional components with hooks")
        *   Any project-specific coding patterns
    *   **Development Environment Constraints:**  Remind Copilot of Bolt's limitations (no `pip`, WebContainer, etc.).
    *   **Test Generation Instructions:** (if applicable)
        *   Testing framework (e.g., "Use React Testing Library and Jest")
        *   Testing focus (e.g., "Prioritize testing component behavior and interactions")
    *   **Code Review Instructions:** (if applicable)
        *   Areas to focus on (e.g., "Pay close attention to accessibility," "Verify adherence to coding style")
    *   **Commit Message Instructions:** (if applicable)
        *   Format (e.g., imperative mood, subject line length, body content)

**Phase 3: Development and Iteration**

**Step 7: Feature-Specific Prompts for Gemini (`gemini/feature-prompts/` - Optional)**

*   **Purpose:**  For larger or more complex features, you can create separate prompt files for Gemini to keep the conversation focused.
*   **Content:**
    *   **Feature Name:** Clearly state the feature you're working on.
    *   **Relevant Context:** Refer to specific sections of the FRD or architectural notes.
    *   **Your Current Understanding:** Explain your initial thoughts or any challenges you're facing.
    *   **Goal:**  Clearly state what you want to achieve.
    *   **Specific Questions for Gemini:** Ask targeted questions to get the guidance you need.

**Step 8: Using Copilot in Your IDE**

*   **Enable Custom Instructions:** Make sure the "Use Instruction Files" option is enabled in your VS Code settings for GitHub Copilot Chat.
*   **Open Relevant Files:** Open the files related to the feature you're working on to provide Copilot with context.
*   **Use Comments and Natural Language:** Guide Copilot with clear comments and natural language prompts within your code.
*   **Iterate:** Use Copilot's suggestions, test your code, and refine it based on the results.

**Step 9: Continuous Documentation**

*   **Update `fileNames.md`:** Keep your file structure map up-to-date as your project evolves.
*   **Refine `functional-requirements.md` and `architectural-notes.md`:**  Modify these documents as needed to reflect any changes in requirements or design decisions.
*   **Improve Gemini Prompts:**  As you learn what works best with Gemini, refine your system prompt and feature-specific prompts.
*   **Update Copilot Instructions:** Adjust your `copilot-instructions.md` file as your coding style, testing practices, or project needs evolve.

**Example File Structure (During Development):**

```
ephemera-codex/
├── .github/
│   └── copilot-instructions.md
├── .gitignore
├── architectural-notes.md
├── functional-requirements.md
├── fileNames.md
├── gemini/
│   ├── gemini_system_prompt.md
│   └── feature-prompts/
│       └── gregos_boot_prompt.md
├── package.json
├── public/
│   └── index.html
├── README.md
├── src/
│   ├── App.js
│   ├── components/
│   │   ├── Dashboard.js
│   │   ├── EthicalConsiderations/
│   │   │   └── EthicalConsiderationsMatrix.js
│   │   ├── GregOSBootScreen/
│   │   │   ├── BootMessage.js
│   │   │   ├── index.js
│   │   │   └── LoadingIndicator.js
│   │   ├── INT3RN4L_3RR0R_ST0RY/
│   │   │   └── Chapter1.js
│   │   ├── Navigation.js
│   │   └── ProjectAmoratus/
│   │       └── QuantumMind.js
│   ├── services/
│   │   └── api.js
│   ├── index.js
│   ├── styles.css
│   └── utils/
│       ├── bootSequence.js
│       ├── constants.js
│       ├── logger.js
│       └── timing.js
└── ...
```

---