# Bolt.New

## Guides/Docs

### 🚀 **Ultimate Guide to bolt.new Prompting**

[https://bolt.new](https://bolt.new)

📚 **Resources & Tools**\
• Bolt Prompter (ChatGPT): [https://chatgpt.com/g/g-tozliiBeO-bolt-prompter](https://chatgpt.com/g/g-tozliiBeO-bolt-prompter)\
• Prompt Inspiration: [https://cursor.directory/](https://cursor.directory/)\
• Issues & Updates: [https://github.com/stackblitz/bolt.new/issues](https://github.com/stackblitz/bolt.new/issues)

🏗️ **Project Structure Best Practices**

1. **Start Broad, Then Drill Down**

   - Begin with overall architecture
   - Use small, focused prompts for specific components
   - Keep token count under 200,000 per prompt

1. **Development Sequence**

   ```
   1. UI Design &amp; Components
   2. Authentication (add after UI is stable)
   3. Database Setup
   4. API Routes
   5. Additional Features
   ```

1. **User Story Prompting**\
   Example format:

   ```
   "I need an app where:
   - As a user, I want to sign in with email
   - As a user, I want to view my dashboard
   - As a signed-in user, I want to update my profile"
   ```

🛠️ **Specific Implementation Tips**

**UI Development**

```
"Create a modern [type] app with:
1. Clean, minimal design
2. Responsive layout
3. Following components: [list them]
4. Using [Tailwind/shadcn/etc] for styling"
```

**Authentication**

- Firebase works well for quick implementation
- Supabase requires more setup but offers good features
- Add auth AFTER basic UI is working

**Database Integration**\
Works well:

- Firebase: Easiest integration, good for beginners
- NoCoDB: Reported successful implementations
- MongoDB: Works with proper abstraction layer

Challenging/WIP:

- Supabase: Some connection issues reported
- AWS: Limited success reports
- External SQL databases: Mixed results

⚡ Pro Tips

1. Controlled Changes

```
"bolt: don't change any code whatsoever. 
Theoretically, if I want to add [feature], 
what code changes would be needed?"
```

2. Error Prevention

- Fork project for fresh start if stuck
- Save working versions before major changes
- Implement database abstraction layer for flexibility

3. Database Setup

- Start with test mode
- Add authentication layer
- Switch to production after testing

4. Image Handling

- Use external CDNs (e.g., Webflow) for images
- Firebase Storage for file uploads
- Avoid direct image hosting in bolt

🎯 Example Full Project Prompt

```
I need a [type] application with these specifications:

Tech Stack:
- Frontend: React with TypeScript
- Styling: Tailwind CSS
- Auth: Firebase
- Database: [choice]

Core Features:
1. User authentication
2. [Main feature]
3. [Secondary features]

Start with creating the main page that includes:
[Detailed page requirements]
```

⚠️ Common Pitfalls to Avoid

1. Don't try to build everything in one prompt
1. Avoid adding auth before UI is stable
1. Don't mix database implementations
1. Test each feature before moving to next
1. Keep backups of working code

🔄 If Things Go Wrong

1. Fork the project for a fresh start
1. Break down the problem into smaller prompts
1. Check GitHub issues for known problems
1. Move to discussions channel for help

📝 Note: bolt.new is actively developing (< 4 weeks in production). These practices are community-sourced and evolving. For latest updates, check the GitHub repository.

______________________________________________________________________

### Using Bolt

Q: What Browsers does Bolt support?

> Bolt works best in Chrome and Chromium browsers. Make sure you are developing in one of these browsers. You can read more [here](https://github.com/stackblitz/bolt.new/issues/2796). Some browser extensions, such as ad blockers, can also interfere with the function of Bolt. If you are experiencing difficulty, a good initial step is to selectively disable browser extensions to see if this resolves the issue.

Q: How do I open a GitHub repository in Bolt?

> Currently, Bolt only has support for public GitHub repositories. Append [bolt.new](https://bolt.new/) with the URL to the public GitHub repository as follows: https://bolt.new/[PUBLIC GITHUB REPOSITORY URL\]

______________________________________________________________________

### Maximizing Token Efficiency: How to Use less Tokens

[Bolt.new](http://bolt.new/) inference uses Anthropic's [Sonnet 3.5 AI model](https://www.anthropic.com/claude/sonnet). We purchase [tokens](https://docs.anthropic.com/en/docs/resources/glossary#tokens) from Anthropic, defined by them as: "the smallest individual units of a language model, and can correspond to words, subwords, characters, or even bytes (in the case of Unicode)." When users interact with Bolt, tokens are consumed in three primary ways: chat messages between the user and the LLM, the LLM writing code, and the LLM reading the existing code to capture any changes made by the user.

Our goal is for Bolt to use as few tokens as possible to accomplish each task. As such, the team is hard at work [continuing to ship](https://github.com/stackblitz/bolt.new/issues/678) product changes that increase token efficiency.

Below are a number of tips you can currently implement to maximize token efficiency:

Avoid Repeated Automated Error "Fix" Attempts

Continuously clicking the automatic "fix" button can lead to unnecessary token consumption. After each attempt, review the result and refine your next request if needed. There are programming challenges that the AI cannot solve automatically, so it is a good idea to do some research and intervene manually if it fails to fix automatically.

Add Error Handling To Your Project

If you find yourself stuck in an error loop, a useful strategy is to prompt the AI to enhance error handling and implement detailed logging throughout the problematic area. The AI excels at inserting robust error logs, even at a granular level, such as between functions or key steps. These logs provide valuable feedback that the AI can use to better understand the root cause of the issue. The additional logging provides more precise information when the error occurs again. With this detailed feedback, the AI can make more accurate adjustments to fix the issue.

Leverage the Rollback Functionality

Use the [rollback feature](https://x.com/stackblitz/status/1844839379270836266) to revert your project to a previous state without consuming tokens. This is essentially an undo button that can take you back to any prior state of your project. This can save time and tokens if something goes wrong with your project. Keep in mind that there is no "redo" function though, so be sure you want to revert before using this feature because it is final: all changes made after the rollback point will be permanently removed.

Make sure the basics of your app are scaffolded before describing the details of more advanced functionality for your site.

Use Specific and Focused Prompts

When prompting the AI, be clear and specific. See [here](https://support.bolt.new/Prompting-Effectively-13fd971055d6801b9af4e965b9ed26e2) for more information on prompting most effectively. Direct the model to focus on certain files or functions rather than the entire codebase, which can improve token usage efficiency. This approach is not a magic fix, but anecdotally we've seen evidence that it helps.

Reduce the Size of your project

As your project grows, more tokens are required to keep the AI in sync with your code. Larger projects (and longer chat conversations) demand more resources for the AI to stay aware of the context, so it's important to be mindful of how project size impacts token usage.

This could be accomplished by breaking a large app into smaller chunks, and glueing it all back together outside of Bolt later. For example, separate backend and frontend into separate projects is a common developer pattern. This could be challenging for less experienced developers.

ADVANCED USERS ONLY:.bolt/ignore

In every bolt project, if you open it in StackBlitz you can edit a file called.bolt/ignore, and in this file you can list out any folders or folders that should be excluded from the AI context window. For example, here is our vite react starter's ignore files: [https://stackblitz.com/edit/vite-shadcn?file=.bolt%2Fignore](https://stackblitz.com/edit/vite-shadcn?file=.bolt%2Fignore). Any files listed there will be completely invisible to the AI, and will clear up space in the context window. You'll need to edit the.bolt/ignore file in StackBlitz and then reopen the project in bolt for the changes to take effect. Please note: hiding files from the AI can have unintended consequences as it is no longer aware of your entire project. This approach is very powerful, but is only recommended for advanced users who can make informed decisions about what can safely be excluded, and understand/resolve issues that may arise from this approach.

#### Advanced Strategy: Reset the AI Context Window

If the AI seems stuck or unresponsive to commands, resetting the AI context window can help. To do this, you will open your and fork your project in StackBlitz, followed by reopening the forked project in Bolt.

- With your project open in Bolt, click Open in StackBlitz at the top-right of page.
- In StackBlitz, click Fork at the top-left of the page. This will create a fork of your current project.
- Rename this project as you see fit.
- Return to the StackBlitz dashboard by clicking the lighting bolt icon at the top-left.
- Open your forked project. Then click Open in bolt.new.
- You should now see your forked project open in Bolt without the previous chat history.

______________________________________________________________________

### Prompting Effectively: How to Talk to Bolt

Q: How can I automatically enhance my prompt?

Q: I only want Bolt to modify a specific file(s), what do I do?

A: Right-click the file(s) of interest in the Bolt code editor and select "[Target file](https://x.com/stackblitz/status/1854205385344999477)" to have Bolt only make changes to those file(s).

Q: I don't want Bolt to modify a specific files(s), what do I do?

User created prompting [guide](https://support.bolt.new/1371ce6babea808ba6ded876e75e5921?pvs=25)

- Start with general architecture, including framework
- Add individual components and features
- Work in details in each component with small, specific prompts
- Use Specific and Focused Prompts:

When prompting the AI, be clear and specific. Direct the model to focus on certain files or functions rather than the entire codebase, which can improve token usage efficiency. This approach is not a magic fix, but anecdotally we've seen evidence that it helps. Some specific prompting strategies that other users have reported as helpful are below, and a ton more can be found in the [comment thread below](https://github.com/stackblitz/bolt.new/issues/678#issuecomment-2460475629)

- If you have specific technologies you want to use (IE Astro, Tailwind, ShadCN), say that in your initial prompt.
- Mention Specific Code Segments or Classes: When possible, refer to specific divs, classes, or functions to guide Bolt to the exact place where you want the changes made. You can do this manually in chat or by highlighting the relevant code in your project and [using the "Ask Bolt" functionality](https://x.com/stackblitz/status/1846953280972509616).
- Use the Prompt Enhancer function: The better the prompt, the higher quality of the output—bolt․new can help you improve your prompts automatically with the [prompt enhancement feature](https://x.com/sulco/status/1846922673739153580)!
- Be Specific About What Should Remain Unchanged: Mention explicitly that no modifications should occur to other parts of the site.
- Batch multiple simple to explain instructions into one message. For example you can ask Bolt to change the color scheme, add mobile responsiveness, and restart the dev server safely all in one message.

#### ADVANCED FEATURE:.bolt/prompt

In every bolt project, if you open it in StackBlitz you can edit a file called [.bolt/prompt](https://x.com/peachpanther/status/1860110256053059962), and you can add custom instructions for the AI. For example, here is our vite react starter's prompt files: [https://stackblitz.com/edit/vite-shadcn?file=.bolt%2Fprompt](https://stackblitz.com/edit/vite-shadcn?file=.bolt%2Fprompt). Any instructions listed there will be taken into account on each prompt inside Bolt. You'll need to edit the.bolt/prompt file in StackBlitz and then reopen the project in bolt for the changes to take effect.

______________________________________________________________________

### The Ultimate Guide to bolt.new Prompting: Build Better Apps Without Deep Technical Knowledge

Building apps used to require deep technical knowledge and months of development time. With bolt.new and modern AI tools, anyone can create full-stack applications. Here's how.

Think of prompts as conversations with an expert developer. The better you explain what you want, the better results you'll get. This guide shows you how.

Use this template to begin:

> "I need a [type] application with: Tech Stack: - Frontend: React with TypeScript - Styling: Tailwind CSS - Auth: Firebase - Database: [choice] Core Features: 1. User authentication 2. [Main feature] 3. [Secondary features] Start with the main page containing: [Detailed page requirements]"

Begin with your end goal and work backwards

Let bolt interpret your vision before diving into specifics

Be intentionally vague sometimes - bolt often surprises you with better solutions

> "I want to build a marketplace app where: - Users list items for sale - Buyers browse and purchase - Sellers track their sales [other stuff you want]"

Sometimes be intentionally vague to let bolt surprise you with creative solutions.

You might get something even better than what you imagined.

Instead of building everything at once, request specific parts:

Break large files into logical components (header, main content, sidebar)

For critical changes use "Do not touch anything else, focus only on this task"

When debugging gets stuck, use "Let's take a step back" to reset

Use.bolt/ignore to restrict which files bolt can access when working on specific sections

Found a design you love? Here's how to use it:

Find and copy component code (or screenshot)

> "Make my navigation menu look like this style: [paste component code/screenshot] Keep the same visual style but change it to include these menu items: - Home - Products - About Us"

Save working components and styles. Use these prompt formats:

> " Using this button style: [paste button code] Create matching components for: - Form inputs - Cards - Alert messages"

> "Look at this card design: [paste code] Create a product grid using the same: - Shadow effects - Border styles - Color scheme - Spacing patterns"

> "don't change any code whatsoever. Theoretically, if I want to add [feature], what code changes would be needed?"

Break into smaller prompts

> "This component worked before: [paste working version] Now it shows this error: [paste error] How do I fix it?"

Save working code and components

Document successful prompts

Build a reference library

Test features independently

Avoid mixing database implementations

Add auth after UI is stable

Keep data requirements clear:

> "I need to save: - User profiles - Product listings - Order history"

External SQL: Mixed results

Start with simple integrations

Watch for over-complication

Request bolt add detailed comments

Explain function purposes

Fork project in StackBlitz frequently

Document architecture decisions

Sometimes the simplest way to explain your vision is to speak it out. Use your device's voice-to-text (Apple Dictation, OpenAI or Super Whisper) to capture detailed ideas naturally.

So what I want is a dashboard that shows all my customer information, and I want it organized kind of like how Gmail does it where you have the list on the left side and when you click on a customer it shows all their details on the right side and make sure there's enough space between everything so it's easy to read and maybe we can have some kind of color coding for different customer status levels like red for urgent issues and green for active customers and yellow for ones we need to follow up with

If its too unclear, you can always optimize it using the one-click prompt optimizer built in bolt.

Speak naturally, use examples

Focus on visuals and user interactions

Don't worry about perfect structure

A: More detail helps. Include examples, reference code, and specific requirements.

A: Copy the code and ask bolt.new to adapt it for your needs. Include CSS and configuration files for best results.

A: Save your favorite components and show them to bolt.new when creating new ones. Ask it to match the style.

A: Break your request into smaller parts. Show examples of what you want.

______________________________________________________________________

# Prompting

## System Prompt

```
You are Bolt, an expert AI assistant and exceptional senior software developer with vast knowledge across multiple programming languages, frameworks, and best practices.

<system_constraints>
  You are operating in an environment called WebContainer, an in-browser Node.js runtime that emulates a Linux system to some degree. However, it runs in the browser and doesn't run a full-fledged Linux system and doesn't rely on a cloud VM to execute code. All code is executed in the browser. It does come with a shell that emulates zsh. The container cannot run native binaries since those cannot be executed in the browser. That means it can only execute code that is native to a browser including JS, WebAssembly, etc.

  The shell comes with \`python\` and \`python3\` binaries, but they are LIMITED TO THE PYTHON STANDARD LIBRARY ONLY This means:

    - There is NO \`pip\` support! If you attempt to use \`pip\`, you should explicitly state that it's not available.
    - CRITICAL: Third-party libraries cannot be installed or imported.
    - Even some standard library modules that require additional system dependencies (like \`curses\`) are not available.
    - Only modules from the core Python standard library can be used.

  Additionally, there is no \`g++\` or any C/C++ compiler available. WebContainer CANNOT run native binaries or compile C/C++ code!

  WebContainer has the ability to run a web server but requires to use an npm package (e.g., Vite, servor, serve, http-server) or use the Node.js APIs to implement a web server.

  IMPORTANT: Prefer using Vite instead of implementing a custom web server.

  IMPORTANT: Git is NOT available.

  IMPORTANT: Prefer writing Node.js scripts instead of shell scripts. The environment doesn't fully support shell scripts, so use Node.js for scripting tasks whenever possible!

  IMPORTANT: When choosing databases or npm packages, prefer options that don't rely on native binaries. For databases, prefer libsql, sqlite, or other solutions that don't involve native code. WebContainer CANNOT execute arbitrary native binaries.

  Available shell commands: cat, chmod, cp, echo, hostname, kill, ln, ls, mkdir, mv, ps, pwd, rm, rmdir, xxd, alias, cd, clear, curl, env, false, getconf, head, sort, tail, touch, true, uptime, which, code, jq, loadenv, node, python3, wasm, xdg-open, command, exit, export, source
</system_constraints>

<code_formatting_info>
  Use 2 spaces for code indentation
</code_formatting_info>

<message_formatting_info>
  You can make the output pretty by using only the following available HTML elements: ${allowedHTMLElements.map((tagName) => `<${tagName}>`).join(', ')}
</message_formatting_info>

<diff_spec>
  For user-made file modifications, a \`<${MODIFICATIONS_TAG_NAME}>\` section will appear at the start of the user message. It will contain either \`<diff>\` or \`<file>\` elements for each modified file:

    - \`<diff path="/some/file/path.ext">\`: Contains GNU unified diff format changes
    - \`<file path="/some/file/path.ext">\`: Contains the full new content of the file

  The system chooses \`<file>\` if the diff exceeds the new content size, otherwise \`<diff>\`.

  GNU unified diff format structure:

    - For diffs the header with original and modified file names is omitted!
    - Changed sections start with @@ -X,Y +A,B @@ where:
      - X: Original file starting line
      - Y: Original file line count
      - A: Modified file starting line
      - B: Modified file line count
    - (-) lines: Removed from original
    - (+) lines: Added in modified version
    - Unmarked lines: Unchanged context

  Example:

  <${MODIFICATIONS_TAG_NAME}>
    <diff path="/home/project/src/main.js">
      @@ -2,7 +2,10 @@
        return a + b;
      }

      -console.log('Hello, World!');
      +console.log('Hello, Bolt!');
      +
      function greet() {
      -  return 'Greetings!';
      +  return 'Greetings!!';
      }
      +
      +console.log('The End');
    </diff>
    <file path="/home/project/package.json">
      // full file content here
    </file>
  </${MODIFICATIONS_TAG_NAME}>
</diff_spec>

<artifact_info>
  Bolt creates a SINGLE, comprehensive artifact for each project. The artifact contains all necessary steps and components, including:

  - Shell commands to run including dependencies to install using a package manager (NPM)
  - Files to create and their contents
  - Folders to create if necessary

  <artifact_instructions>
    1. CRITICAL: Think HOLISTICALLY and COMPREHENSIVELY BEFORE creating an artifact. This means:

      - Consider ALL relevant files in the project
      - Review ALL previous file changes and user modifications (as shown in diffs, see diff_spec)
      - Analyze the entire project context and dependencies
      - Anticipate potential impacts on other parts of the system

      This holistic approach is ABSOLUTELY ESSENTIAL for creating coherent and effective solutions.

    2. IMPORTANT: When receiving file modifications, ALWAYS use the latest file modifications and make any edits to the latest content of a file. This ensures that all changes are applied to the most up-to-date version of the file.

    3. The current working directory is \`${cwd}\`.

    4. Wrap the content in opening and closing \`<boltArtifact>\` tags. These tags contain more specific \`<boltAction>\` elements.

    5. Add a title for the artifact to the \`title\` attribute of the opening \`<boltArtifact>\`.

    6. Add a unique identifier to the \`id\` attribute of the of the opening \`<boltArtifact>\`. For updates, reuse the prior identifier. The identifier should be descriptive and relevant to the content, using kebab-case (e.g., "example-code-snippet"). This identifier will be used consistently throughout the artifact's lifecycle, even when updating or iterating on the artifact.

    7. Use \`<boltAction>\` tags to define specific actions to perform.

    8. For each \`<boltAction>\`, add a type to the \`type\` attribute of the opening \`<boltAction>\` tag to specify the type of the action. Assign one of the following values to the \`type\` attribute:

      - shell: For running shell commands.

        - When Using \`npx\`, ALWAYS provide the \`--yes\` flag.
        - When running multiple shell commands, use \`&&\` to run them sequentially.
        - ULTRA IMPORTANT: Do NOT re-run a dev command if there is one that starts a dev server and new dependencies were installed or files updated! If a dev server has started already, assume that installing dependencies will be executed in a different process and will be picked up by the dev server.

      - file: For writing new files or updating existing files. For each file add a \`filePath\` attribute to the opening \`<boltAction>\` tag to specify the file path. The content of the file artifact is the file contents. All file paths MUST BE relative to the current working directory.

    9. The order of the actions is VERY IMPORTANT. For example, if you decide to run a file it's important that the file exists in the first place and you need to create it before running a shell command that would execute the file.

    10. ALWAYS install necessary dependencies FIRST before generating any other artifact. If that requires a \`package.json\` then you should create that first!

      IMPORTANT: Add all required dependencies to the \`package.json\` already and try to avoid \`npm i <pkg>\` if possible!

    11. CRITICAL: Always provide the FULL, updated content of the artifact. This means:

      - Include ALL code, even if parts are unchanged
      - NEVER use placeholders like "// rest of the code remains the same..." or "<- leave original code here ->"
      - ALWAYS show the complete, up-to-date file contents when updating files
      - Avoid any form of truncation or summarization

    12. When running a dev server NEVER say something like "You can now view X by opening the provided local server URL in your browser. The preview will be opened automatically or by the user manually!

    13. If a dev server has already been started, do not re-run the dev command when new dependencies are installed or files were updated. Assume that installing new dependencies will be executed in a different process and changes will be picked up by the dev server.

    14. IMPORTANT: Use coding best practices and split functionality into smaller modules instead of putting everything in a single gigantic file. Files should be as small as possible, and functionality should be extracted into separate modules when possible.

      - Ensure code is clean, readable, and maintainable.
      - Adhere to proper naming conventions and consistent formatting.
      - Split functionality into smaller, reusable modules instead of placing everything in a single large file.
      - Keep files as small as possible by extracting related functionalities into separate modules.
      - Use imports to connect these modules together effectively.
  </artifact_instructions>
</artifact_info>

NEVER use the word "artifact". For example:
  - DO NOT SAY: "This artifact sets up a simple Snake game using HTML, CSS, and JavaScript
```

______________________________________________________________________

## Comprehensive Software Planning Meta Prompt

This meta prompt outlines a systematic approach for Bolt to create a detailed software project plan. It includes analyzing requirements, defining structure, designing UI, planning implementation, and mapping out how the chosen tech stack fits into the development process.

```
You are an AI assistant tasked with creating a comprehensive plan for developing a software project based on a given description. Your goal is to analyze the project requirements, design the structure and UI, and outline the basic functionality for each component.

You will be provided with the following input variables:

<project_description>
{{PROJECT_DESCRIPTION}}
</project_description>

<project_stack>
{{PROJECT_STACK}}
</project_stack>

<additional_details>
{{ADDITIONAL_DETAILS}}
</additional_details>

Follow these steps to create a detailed project plan:

1. Analyze the project description:
   - Identify the main features and requirements of the project
   - Determine the target audience and use cases
   - List any constraints or special considerations mentioned

2. Define the project structure:
   - Outline the main components or modules of the project
   - Describe how these components will interact with each other
   - Specify any external integrations or APIs required

3. Design the UI and functionality:
   - Create a high-level description of the user interface
   - List and describe each page or screen of the application
   - Outline the basic functionality for each page or component

4. Create an implementation plan:
   - Break down the project into smaller tasks or milestones
   - Suggest a development timeline or sprint structure
   - Identify potential challenges and propose solutions

5. Consider the project stack and additional details:
   - Explain how the specified project stack will be utilized
   - Incorporate any additional details provided into the plan

Present your project plan in the following format:

<project_plan>
<summary>
Provide a brief overview of the project and its main goals.
</summary>

<analysis>
Present your analysis of the project description, including main features, target audience, and any constraints.
</analysis>

<structure>
Outline the project structure, including main components and their interactions.
</structure>

<ui_design>
Describe the overall user interface design and list each page or screen with its basic functionality.
</ui_design>

<implementation>
Present the implementation plan, including tasks, timeline, and potential challenges.
</implementation>

<stack_utilization>
Explain how the specified project stack will be used in the development process.
</stack_utilization>

<additional_considerations>
Address any additional details or considerations provided in the input.
</additional_considerations>
</project_plan>

Ensure that your plan is comprehensive, well-structured, and takes into account all the information provided in the input variables. Be creative in your design choices while staying true to the project requirements.
```

## Tips

### bolt.new - Search / X

In my experience working with [http://bolt.new](https://t.co/Sbl8h5wFfc), successful execution comes through precise problem-solving - knowing exactly what's breaking and where. Being a developer helps here, as it's easier to pinpoint issues and fix them. But if you're a non-developer like me, I've found that setting up Claude as your "software architect" is the key to achieving this precision.

Building on my previous tip about having a detailed FRD (Functional Requirements Document), here's the structured system I've developed:

File and Folder Structure in Bolt:

Start with a File Structure Map. I ask bolt to create a "[http://fileNames.md](https://t.co/BHerkMgAgY)" that lists every file and maintains the folder hierarchy.

Each entry includes a one-line description of the component's purpose and functionality.

This becomes our project's map.

Claude Projects:

Set Up a Dedicated "Issue Resolution" Project in Claude.

I created a separate Claude project specifically for handling fixes and updates.

Under project knowledge, I've added:

- The complete file structure (from [http://fileNames.md](https://t.co/BHerkMgAgY))
- Master functional requirements document
- FRD split by components (based on user flow)
- A document explaining [http://bolt.new](https://t.co/Sbl8h5wFfc)'s capabilities Streamlined Problem-Solving: For every fix or new feature, I go to this Claude project and use a specific prompt structure.

Here's my workflow:

- First, I set the context with my "system prompt".
- Then, for each fix/feature request, I use the "execution prompt". <both prompts are given below> This specific format I use to describe the issue/feature, which helps Claude write optimized prompts for [http://bolt.new](https://t.co/Sbl8h5wFfc), identify relevant files, and suggest the most token-efficient approach and even provide you with the exact steps to fix the issue.

Using.bolt/ignore: I worked with Claude to identify files that don't need to be in the LLM's context and added them to.bolt/ignore. This significantly reduced token usage while maintaining development efficiency. Note that we need to do this multiple times, depending on what you're fixing. The result? I've essentially created a two-tier system:

- Claude acts as the "software architect," analyzing issues and designing solutions
- [http://bolt.new](https://t.co/Sbl8h5wFfc) becomes the "developer," implementing those solutions efficiently This approach has transformed my development process. Instead of getting stuck in token limits or unclear prompts, I can focus on building and improving features.

______________________________________________________________________

**Core Problem:**

The central challenge being addressed is how a non-developer can effectively troubleshoot and implement features within a development environment (Bolt.new) without the inherent understanding of code and system architecture that developers possess.

**The Solution: Claude as a "Software Architect"**

The genius of this approach lies in leveraging the capabilities of a large language model (Claude) to bridge the gap in technical expertise. Instead of trying to directly manipulate the codebase, the author uses Claude to:

- **Understand the system:** By feeding Claude with the file structure, requirements, and platform capabilities, it gains a comprehensive understanding of the project.
- **Diagnose problems:** When an issue arises, the structured prompts allow the author to clearly communicate the problem to Claude.
- **Design solutions:** Claude analyzes the information and proposes solutions, including identifying relevant files and suggesting the most efficient implementation strategy.
- **Generate instructions for the "developer" (Bolt):** Claude effectively translates the high-level problem into specific instructions that Bolt.new can understand and execute.

**Key Components of the System and Why They Work:**

1. **Detailed FRD (Functional Requirements Document):** This is the foundation. A well-defined FRD provides the blueprint for the project, allowing both the human and the AI to understand the intended functionality.

1. **File Structure Map (`fileNames.md`):**

   - **Provides a bird's-eye view:** This document acts as a roadmap of the project's codebase.
   - **Enhances communication with Claude:** It helps Claude understand the organization and relationships between different components.
   - **Facilitates issue localization:** When describing a problem, referencing specific files becomes much easier.

1. **Dedicated Claude "Issue Resolution" Project:**

   - **Contextual Isolation:** Keeping issue resolution separate prevents confusion and allows Claude to focus on troubleshooting and development tasks.
   - **Centralized Knowledge Base:** Storing all relevant project information within this project ensures Claude has the necessary context for every request.

1. **Project Knowledge:** Feeding Claude with specific information is crucial for its effectiveness:

   - **Complete File Structure:** As mentioned above, this provides architectural context.
   - **Master FRD:** Reinforces the overall goals and functionality.
   - **FRD Split by Components:** This is a clever step. Breaking down the FRD by user flow allows for more targeted analysis of specific feature areas.
   - **Bolt.new Capabilities Document:** Ensures Claude understands the limitations and possibilities within the Bolt platform, leading to more feasible solutions.

1. **Structured Prompt Workflow:**

   - **"System Prompt":** Sets the stage and provides general instructions to Claude, establishing its role as the "software architect."
   - **"Execution Prompt":** This is where the specific problem or feature request is detailed. The structure of this prompt is key to eliciting the desired response from Claude. By providing clear context and describing the issue precisely, the author guides Claude towards generating optimized prompts for Bolt.

1. **`.bolt/ignore`:**

   - **Token Optimization:** This is a practical consideration for managing costs and improving efficiency with LLMs. By excluding irrelevant files, the context window for Claude remains focused on the necessary information.
   - **Improved Performance:** Reducing the context size can also lead to faster response times from Claude.
   - **Iterative Refinement:** The acknowledgment that this is an ongoing process highlights the adaptive nature of this approach.

1. **Two-Tier System Analogy (Claude as Architect, Bolt as Developer):**

   - **Clear Division of Labor:** This analogy simplifies the complex process. Claude handles the planning and design, while Bolt executes the instructions.
   - **Empowerment for Non-Developers:** It allows individuals without coding expertise to contribute meaningfully to development by focusing on problem definition and leveraging AI for the technical aspects.

**Why This Approach is Powerful:**

- **Democratizes Development:** It makes development more accessible to individuals without traditional coding backgrounds.
- **Increases Efficiency:** By leveraging Claude for analysis and solution design, the process becomes more streamlined and less prone to trial-and-error.
- **Reduces Errors:** Precise problem-solving, guided by Claude's insights, leads to more accurate fixes and feature implementations.
- **Optimizes Resource Usage:** The `.bolt/ignore` strategy demonstrates a focus on practical considerations like token management.
- **Focus on Building:** By offloading the technical complexities to Claude, the author can concentrate on the higher-level aspects of building and improving features.

**In conclusion, this is a well-thought-out and practical system for leveraging AI to enhance the development process for non-developers. It demonstrates a deep understanding of both the capabilities of LLMs and the challenges faced by those without traditional coding skills. The structured approach, combined with the clever use of Claude as a "software architect," makes this a valuable strategy for anyone working with platforms like Bolt.new.**

______________________________________________________________________

**Understanding the Core Shift:**

The main difference is that GitHub Copilot is deeply integrated within your code editor (like VS Code), acting as a real-time coding assistant. Google Gemini, on the other hand, is more akin to Claude, functioning as a general-purpose AI you interact with via chat or its API. You'll leverage both for different aspects of the workflow.

**Mapping the Components:**

Here's how we can map the elements of your existing system:

- **Claude as "Software Architect" -> Google Gemini:** Gemini will take on the role of analyzing issues, suggesting solutions, identifying relevant files, and helping you understand the problem at a higher level.
- **Bolt.new as "Developer" -> GitHub Copilot:** Copilot will be your primary tool for implementing the solutions, writing code, and making changes within your codebase.

**Steps to Implement with GitHub Copilot and Google Gemini:**

**1. File and Folder Structure in Bolt -> File and Folder Structure in your Git Repository:**

- **Maintain your `fileNames.md`:** You can still manually create and maintain this file. It's a valuable piece of documentation, regardless of the AI tools you use.
- **Leverage Git for Hierarchy:** GitHub (and Git in general) naturally maintains the folder hierarchy of your project. This is inherently tracked.

**2. Claude Projects -> Gemini Conversations or Documents:**

- **Dedicated Gemini Conversation:** Create a new chat conversation in Gemini specifically for issue resolution for this project. This helps keep the context focused.
- **Google Docs or similar:** Alternatively, you could maintain a Google Doc dedicated to "Issue Resolution" where you paste relevant information and your interactions with Gemini.

**3. Project Knowledge in Gemini:**

- **The complete file structure (`fileNames.md`):** Copy and paste the content of your `fileNames.md` into the Gemini conversation at the start or when introducing a new issue.
- **Master functional requirements document:** Share relevant sections or the entire document with Gemini when setting the context for a problem.
- **FRD split by components (based on user flow):** Similarly, share the specific component's FRD with Gemini when working on issues related to that component.
- **A document explaining Bolt.new's capabilities -> A document explaining your Project's Architecture/Specifics:** Since you're using Copilot directly within your codebase, you'll need to provide Gemini with context about any unique patterns, libraries, or architectural decisions in your project. This replaces the need to explain Bolt.new's capabilities.

**4. Streamlined Problem-Solving Workflow:**

- **System Prompt (Adapt for Gemini):**

  ```
  "You are an experienced software architect helping a developer (using GitHub Copilot) understand and fix issues in a software project. The project has the following file structure: [paste content of fileNames.md]. The core functionality is described in this functional requirements document: [briefly describe the FRD or link to it if hosted online]. When analyzing issues, consider the architectural decisions and best practices for maintainable code. Focus on providing clear explanations, identifying relevant files, and suggesting efficient approaches that GitHub Copilot can help implement."
  ```

- **Execution Prompt (Adapt for Gemini):**

  ```
  "**Issue:** [Clearly and concisely describe the issue you are facing. Be specific about what's breaking, where you're observing the problem, and any error messages.]

  **Relevant Context (User Flow/Component):** [Mention the specific user flow or component involved, potentially referencing sections of your FRD].

  **My Current Understanding:** [Briefly explain what you've already tried or what you suspect might be the cause. Even if you're not sure, this helps Gemini understand your thought process.]

  **Goal:** [State what you want to achieve - fix the bug, implement the new feature, etc.]

  **Can you help me pinpoint the exact files involved and suggest the most efficient way to fix this, considering GitHub Copilot will be used for implementation?"
  ```

**How Gemini Helps Copilot:**

- **Identify Relevant Files:** Gemini will analyze the issue description and your project knowledge to suggest which files you should be working on.
- **Suggest Approaches:** Gemini can outline the steps needed to address the issue, considering best practices.
- **Explain Concepts:** If you're unsure about a particular piece of code or concept, you can ask Gemini for clarification.
- **Help Refine Prompts for Copilot (Indirectly):** By understanding the problem better through Gemini, you'll be able to write more effective natural language comments within your code, guiding Copilot to generate the correct code.

**5. Using `.bolt/ignore` -> Using `.gitignore` and Context Awareness in Copilot:**

- **`.gitignore`:** Utilize your `.gitignore` file to exclude unnecessary files and directories from your Git repository. This helps keep your project cleaner and reduces the noise Copilot might consider.
- **Copilot's Context Window:** Copilot is intelligent and considers the code in your currently open files and surrounding files. By focusing on the relevant files identified by Gemini, you naturally guide Copilot to the appropriate context.
- **Strategic File Opening:** When working on a specific issue, open only the files that Gemini suggests are relevant. This limits the scope of Copilot's context and improves its suggestions.

**Workflow Example:**

1. **Issue Arises:** You notice a bug in the user registration process.
1. **Gemini Interaction:**
   - You go to your dedicated Gemini conversation.
   - You provide the system prompt (if needed for a new session).
   - You use the execution prompt:

     ```
     "**Issue:** Users are not receiving confirmation emails after registration.

     **Relevant Context (User Flow/Component):** This is happening in the user registration flow, specifically after the 'Create Account' button is clicked. This relates to section 3.2 of the FRD.

     **My Current Understanding:** I suspect there might be an issue with the email sending service integration or the logic that triggers the email sending.

     **Goal:** I need to fix the email confirmation issue. Can you help me pinpoint the exact files involved in sending the confirmation email and suggest the most efficient way to debug this, considering I'll be using GitHub Copilot to implement the fix?"
     ```

   - **Gemini's Response:** Gemini might suggest looking at files like `user_registration.py`, `email_service.py`, and any configuration files related to email settings. It might suggest debugging the email sending function or checking the email queue.
1. **Copilot Implementation:**
   - You open the files Gemini suggested in your code editor.
   - You start typing comments or code, and Copilot will provide suggestions based on the context.
   - You can use comments like: `// Send the confirmation email to the user` and Copilot will likely suggest the relevant code based on your project.
   - As you debug, you can ask Gemini further questions if needed.

**Benefits of this Approach:**

- **Leverages Copilot's Strengths:** You're using Copilot for what it's best at: real-time code assistance and generation within your IDE.
- **Utilizes Gemini's Analytical Abilities:** Gemini provides the higher-level architectural understanding and problem-solving guidance.
- **Clear Separation of Concerns:** Gemini helps you understand the "what" and "why," while Copilot helps you with the "how."
- **Improved Efficiency:** By focusing on the relevant files and having a clear understanding of the problem, you can use Copilot more effectively.

**Key Differences and Considerations:**

- **Context Management:** Unlike Claude's "project knowledge," Gemini relies on the context within your conversation. Be sure to provide relevant information with each new issue.
- **Real-time Code Assistance:** Copilot's integration within the IDE is a significant advantage for implementation.
- **Prompting for Copilot:** You'll guide Copilot through your coding by writing clear and descriptive comments and following logical coding patterns.
- **Iterative Process:** Like your previous setup, this will be an iterative process of learning how to best communicate with both Gemini and Copilot.

By combining the strengths of Google Gemini and GitHub Copilot, you can effectively recreate a similar workflow to your previous setup, empowering you to solve problems and build features more efficiently, even as a non-developer. Remember to experiment with your prompts and refine your process over time.

______________________________________________________________________

**Phase 1: Initial Setup and Knowledge Gathering**

1. **Set up your Git Repository and Project:**

   - Ensure your project is initialized as a Git repository. This is fundamental for Copilot's functionality and for maintaining your file structure.

1. **Create `fileNames.md` (Manual):**

   - In the root of your project, create a file named `fileNames.md`.
   - Manually list all the files and folders in your project, maintaining the hierarchy. For each file, add a one-line description of its purpose and functionality.
   - **Example:**

     ```markdown
     ├── src/
     │   ├── components/
     │   │   ├── user_profile.js - Handles the display and editing of user profile information.
     │   │   ├── navigation.js -  Manages the main application navigation.
     │   ├── services/
     │   │   ├── api_client.js -  Handles communication with the backend API.
     │   ├── App.js -  Main application entry point.
     ├── public/
     │   ├── index.html -  Main HTML file.
     ├── package.json -  Project dependencies and scripts.
     ```

1. **Document your Functional Requirements (FRD):**

   - Create a comprehensive Functional Requirements Document. This can be a separate document (e.g., a Word doc, Google Doc, or Markdown file) or even maintained within your Git repository.
   - **Key elements to include:**
     - Overall project goals
     - User stories or use cases
     - Detailed descriptions of features and functionalities
     - User flows (how users interact with the application)

1. **Split FRD by Components (Optional but Recommended):**

   - If your FRD is large, consider creating separate documents or sections within your FRD that focus on specific user flows or components. This will make it easier to provide targeted context to Gemini.

1. **Prepare Project Architecture/Specifics Document:**

   - Create a document (or a section within your FRD) that explains the key architectural decisions, design patterns, important libraries, and any unique conventions used in your project. This will be your substitute for the "Bolt.new capabilities document."

1. **Set up your Gemini Environment:**

   - Open Google Gemini (through the web interface or API, depending on your preference).
   - Create a new chat conversation that will be dedicated to issue resolution for this specific project.

**Phase 2: Establishing the Workflow**

7. **Define your "System Prompt" for Gemini (One-Time Setup):**
   - In your dedicated Gemini conversation, start with a prompt similar to this (adapt as needed):

     ```
     "You are an experienced software architect helping a developer (using GitHub Copilot) understand and fix issues in the following software project.

     **Project File Structure:**
     [Paste the entire content of your `fileNames.md` here]

     **Core Functionality Overview (Brief Summary of FRD):**
     [Provide a concise summary of the project's main goals and functionality. You can also link to your FRD document if it's hosted online.]

     **Key Architectural Notes and Conventions:**
     [Paste the content of your "Project Architecture/Specifics" document here]

     When analyzing issues, consider the project structure, architectural decisions, and best practices for maintainable code. Focus on providing clear explanations, identifying relevant files, and suggesting efficient approaches that GitHub Copilot can help implement."
     ```

**Phase 3: Problem Solving and Feature Implementation**

8. **Identify a Fix or Feature Request:** Determine the specific issue you need to address or the new feature you want to implement.

1. **Formulate your "Execution Prompt" for Gemini:**

   - In your dedicated Gemini conversation, use a structured prompt like this:

     ```
     **Issue/Feature:** [Clearly and concisely describe the issue you are facing or the feature you want to implement. Be specific about what's breaking, where you're observing the problem, any error messages, or the desired functionality.]

     **Relevant Context (User Flow/Component):** [Mention the specific user flow or component involved. If applicable, reference sections of your FRD or the split component FRD.]

     **My Current Understanding/Initial Thoughts:** [Briefly explain what you've already tried, what you suspect might be the cause (for fixes), or your initial ideas for implementation (for features). Even if you're not entirely sure, this helps Gemini understand your starting point.]

     **Goal:** [State clearly what you want to achieve - fix the bug, implement the new feature, etc.]

     **Considering I'll be using GitHub Copilot for implementation, can you help me:**
     *   **Pinpoint the exact file(s) I should be focusing on?**
     *   **Suggest the most efficient approach or steps to take?**
     *   **Explain any relevant concepts or code sections I should be aware of?**
     ```

1. **Analyze Gemini's Response:** Carefully read Gemini's suggestions. It should help you:

   - Understand the root cause of the issue or the best way to approach the feature.
   - Identify the relevant files in your project.
   - Provide a high-level plan of action.

1. **Implement with GitHub Copilot:**

   - Open your code editor (e.g., VS Code) with the relevant project.
   - **Open the files Gemini identified.** This is crucial for providing Copilot with the correct context.
   - Start working on the identified files. Use natural language comments to guide Copilot.
     - **Example (Fix):** `// Bug: Confirmation email not sending. Need to check the email service integration here.`
     - **Example (Feature):** `// Feature: Implement user profile update. Need to handle the form submission and API call.`
   - As you type, Copilot will provide code suggestions. Review and accept or modify them as needed.
   - **Focus on writing clear, well-structured code.** This helps Copilot provide better suggestions.
   - If you get stuck or Copilot's suggestions are not helpful, go back to Gemini with more specific questions.

1. **Iterate and Refine:** Software development is rarely linear. You might need to go back and forth between Gemini and Copilot as you encounter new challenges or refine your approach.

**Phase 4: Maintaining Efficiency and Reducing Token Usage (Implicit with Copilot)**

13. **Leverage `.gitignore`:**

    - Ensure your `.gitignore` file is properly configured to exclude unnecessary files and directories (e.g., node_modules, build directories, sensitive configuration files). This helps keep your Git repository clean and indirectly helps Copilot focus on relevant code.

01. **Focus Copilot's Context:** By opening only the files relevant to the current task (as identified by Gemini), you naturally limit the scope of Copilot's context, leading to more focused and relevant suggestions.

01. **Continuous Learning and Prompt Refinement:** As you work with Gemini and Copilot, pay attention to what prompts work best for eliciting the information you need. Refine your "Execution Prompt" over time to be more effective.

**Example Scenario: Fixing the User Registration Email Issue**

1. **Execution Prompt to Gemini:**

   ```
   **Issue:** Users are not receiving confirmation emails after registration.

   **Relevant Context (User Flow/Component):** This is happening in the user registration flow, specifically after the 'Create Account' button is clicked. This relates to section 3.2 of the FRD.

   **My Current Understanding/Initial Thoughts:** I suspect there might be an issue with the email sending service integration in `src/services/api_client.js` or the logic that triggers the email sending in `src/components/user_registration.js`.

   **Goal:** I need to fix the email confirmation issue. Can you help me:
   *   Pinpoint the exact file(s) I should be focusing on?
   *   Suggest the most efficient approach or steps to take?
   *   Explain how the email sending process should work based on the architecture?
   ```

1. **Gemini's Response (Example):** Gemini might suggest checking `src/components/user_registration.js` to see how the registration form is handled and if the email sending function is called. It might also suggest looking at `src/services/api_client.js` to verify the email sending function and its integration with the email service.

1. **Implementation with Copilot:**

   - Open `src/components/user_registration.js`.
   - Type a comment: `// Check if the sendConfirmationEmail function is called after successful registration.` Copilot might suggest the relevant code block.
   - Open `src/services/api_client.js`.
   - Type a comment: `// Verify the implementation of the sendConfirmationEmail function and its parameters.` Copilot will likely provide suggestions based on your existing code.

______________________________________________________________________

## Detailed Example of a Functional Requirements Document (FRD)

This example FRD outlines the functional requirements for a **Simple To-Do List Application**.

**1. Introduction**

**1.1 Purpose**

This document outlines the functional requirements for a Simple To-Do List Application. It describes the features and functionalities that the application must provide to its users. This document serves as a guide for the development team and ensures a common understanding of the application's intended behavior among stakeholders.

**1.2 Scope**

This document covers the core functionalities of the To-Do List application, including user management, task creation, task management, and basic organization features. It does not cover aspects such as advanced collaboration features, detailed reporting, or integration with external services (unless explicitly stated).

**1.3 Intended Audience**

This document is intended for the following individuals:

- Project Manager
- Development Team (Developers, Designers, Testers)
- Product Owner
- Stakeholders

**2. Overall Description**

**2.1 Product Perspective**

The Simple To-Do List Application is a standalone application designed to help users manage their tasks effectively. It will be a web-based application accessible through standard web browsers. The application aims to provide a user-friendly and intuitive interface for managing personal tasks.

**2.2 User Classes and Characteristics**

- **General User:** Any individual who wants to create, manage, and organize their personal tasks. General users are expected to have basic computer literacy and familiarity with web applications.

**2.3 Operating Environment**

- **Platform:** Web-based application accessible through modern web browsers (Chrome, Firefox, Safari, Edge).
- **Responsive Design:** The application should be responsive and adapt to different screen sizes (desktops, tablets, and mobile devices).
- **Accessibility:** The application should strive to meet basic accessibility guidelines (WCAG) to be usable by a wider audience.

**2.4 Design and Implementation Constraints**

- **Technology Stack:** (Example - This would be defined based on the project's choices)
  - Frontend: React or Vue.js
  - Backend: Node.js with Express or Python with Django/Flask
  - Database: MongoDB or PostgreSQL
- **Security:** User data must be stored securely, and standard security practices should be followed to prevent unauthorized access.
- **Performance:** The application should be responsive and load quickly.
- **Scalability:** While initially for individual use, the application should be designed with potential future scalability in mind.

**2.5 Assumptions and Dependencies**

- It is assumed that users have access to a stable internet connection.
- The development team has the necessary skills and resources to implement the requirements.
- The user interface design will be provided separately.

**3. Specific Requirements**

This section details the specific functional requirements of the To-Do List Application. Each requirement is identified with a unique ID and includes a description, priority, and any relevant input, processing, and output.

**3.1 User Management**

| Requirement ID | Description                                                                     | Priority    | Input                                       | Processing                                                                                         | Output                                                     |
| :------------- | :------------------------------------------------------------------------------ | :---------- | :------------------------------------------ | :------------------------------------------------------------------------------------------------- | :--------------------------------------------------------- |
| UM-001         | **User Registration:** The system shall allow new users to register an account. | Must Have   | Username, Email, Password, Confirm Password | Verify email format, password complexity, and matching passwords. Store user credentials securely. | Successful registration message, login screen redirection. |
| UM-002         | **User Login:** Registered users shall be able to log in to the application.    | Must Have   | Username/Email, Password                    | Authenticate user credentials against stored data.                                                 | Access to the main application interface.                  |
| UM-003         | **User Logout:** Logged-in users shall be able to securely log out.             | Must Have   | Click on "Logout" button                    | Invalidate user session.                                                                           | Redirection to the login screen.                           |
| UM-004         | **Password Reset:** Users shall be able to reset their password if forgotten.   | Should Have | Email address                               | Send a password reset link to the provided email address.                                          | Confirmation message, email with reset link.               |

**3.2 Task Management**

| Requirement ID | Description                                                                    | Priority    | Input                                                                        | Processing                                                               | Output                                                                 |
|:------------- |:----------------------------------------------------------------------------- |:---------- |:--------------------------------------------------------------------------- |:----------------------------------------------------------------------- |:--------------------------------------------------------------------- |
| TM-001         | **Create Task:** Users shall be able to create new tasks.                      | Must Have   | Task Title, Description (optional)                                           | Store the task details associated with the logged-in user.               | Confirmation message, new task added to the task list.                 |
| TM-002         | **View Task List:** Users shall be able to view a list of their created tasks. | Must Have   | Login                                                                        | Retrieve all tasks associated with the logged-in user from the database. | Display of the task list, including title and status.                  |
| TM-003         | **Mark Task as Complete:** Users shall be able to mark a task as complete.     | Must Have   | Click on "Complete" button for a task                                        | Update the task status to "Completed" in the database.                   | Visual indication of task completion (e.g., strikethrough, checkmark). |
| TM-004         | **Edit Task:** Users shall be able to edit the details of an existing task.    | Should Have | Click on "Edit" button for a task, Modified Task Title, Modified Description | Update the task details in the database.                                 | Confirmation message, updated task details in the task list.           |
| TM-005         | **Delete Task:** Users shall be able to delete a task.                         | Should Have | Click on "Delete" button for a task                                          | Remove the task from the database.                                       | Confirmation message, task removed from the task list.                 |

**3.3 Task Organization**

| Requirement ID | Description                                                                                           | Priority    | Input                                             | Processing                                                                                   | Output                                          |
|:------------- |:---------------------------------------------------------------------------------------------------- |:---------- |:------------------------------------------------ |:------------------------------------------------------------------------------------------- |:---------------------------------------------- |
| TO-001         | **Prioritize Task:** Users shall be able to assign a priority level to a task.                        | Could Have  | Select a priority level (e.g., High, Medium, Low) | Store the priority level associated with the task.                                           | Visual indication of priority in the task list. |
| TO-002         | **Filter Tasks:** Users shall be able to filter tasks based on their status (All, Active, Completed). | Should Have | Select a filter option                            | Retrieve and display tasks matching the selected status for the logged-in user.              | Display of the filtered task list.              |
| TO-003         | **Sort Tasks:** Users shall be able to sort tasks by creation date or priority.                       | Could Have  | Select a sorting option                           | Retrieve and display tasks sorted according to the selected criteria for the logged-in user. | Display of the sorted task list.                |

**4. Non-Functional Requirements**

**4.1 Performance Requirements**

- **Response Time:** The application should respond to user actions (e.g., creating a task, marking as complete) within 2 seconds.
- **Load Time:** The initial page load should not exceed 3 seconds.

**4.2 Security Requirements**

- **Password Storage:** User passwords shall be stored securely using industry-standard hashing algorithms.
- **Data Protection:** Sensitive user data should be protected from unauthorized access and modification.
- **Session Management:** User sessions should be managed securely to prevent unauthorized access.

**4.3 Usability Requirements**

- **Intuitive Interface:** The application should have a clean and intuitive user interface that is easy to navigate and understand.
- **Clear Feedback:** The application should provide clear feedback to users after each action.
- **Accessibility:** The application should adhere to basic accessibility guidelines.

**4.4 Reliability Requirements**

- **Availability:** The application should be available to users with minimal downtime.
- **Data Integrity:** The application should ensure the integrity and consistency of user data.

**5. Future Enhancements (Out of Scope for Initial Release)**

- Collaboration features (sharing lists, assigning tasks).
- Integration with calendar applications.
- Mobile application versions.
- Advanced reporting and analytics.

**6. Glossary**

| Term | Definition                                                    |
|:--- |:------------------------------------------------------------ |
| Task | A single unit of work or activity that needs to be completed. |
| User | An individual who interacts with the To-Do List Application.  |
| FRD  | Functional Requirements Document.                             |
| WCAG | Web Content Accessibility Guidelines.                         |

______________________________________________________________________
