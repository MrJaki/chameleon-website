# Chameleon

**Build, modify, and iterate on React applications using natural language.**

Chameleon is an AI-powered desktop development environment designed to make application development more accessible without removing the power and flexibility of real source code.

Instead of manually creating files, components, routes, styles, and configuration, you can describe what you want in natural language and let Chameleon plan and implement the changes directly in your project.

Chameleon works with modern **React + TypeScript + Vite** applications and can use either local AI models or cloud-based AI providers.

> **Chameleon is currently under active development.**

---

##  Features

###  AI-Powered Development

Describe what you want to build or change using natural language.

For example:

> "Create a dashboard with a sidebar, statistics cards, a recent activity table, and a settings page."

Chameleon can analyze the request, create an implementation plan, generate the required files, and update the application.

You don't need to manually decide which files need to be created or modified.

---

###  Planner + Coder Architecture

Chameleon separates planning from implementation.

The **Planner** analyzes the user's request and determines what needs to change.

The **Coder** then implements the planned changes.

A typical workflow looks like:

```text
User Request
     │
     ▼
┌─────────────┐
│   Planner   │
└──────┬──────┘
       │
       ▼
Implementation Plan
       │
       ▼
┌─────────────┐
│    Coder    │
└──────┬──────┘
       │
       ▼
Project Files
       │
       ▼
Live Preview
```

This separation helps prevent the AI from blindly modifying unrelated files and provides a more structured development workflow.

---

###  Live Preview

Chameleon can run your React application and display the result directly inside the application.

Changes can be inspected without constantly switching between your editor and browser.

The preview is designed to work alongside Chameleon's development tools, allowing you to:

* View your application
* Inspect elements
* Select components
* Modify properties
* Preview changes
* Iterate quickly

---

###  Visual Editor

Chameleon includes a visual editing environment for interacting with the generated application.

You can select elements directly from the preview and inspect their properties.

Depending on the element, Chameleon can work with properties such as:

* Text
* Background
* Colors
* Spacing
* Border radius
* Dimensions
* Links
* Inputs
* Containers
* Components

The goal is to bridge the gap between traditional visual editors and actual source code.

Instead of generating a separate representation of your application, Chameleon works with the application's real files.

---

###  Project Structure Awareness

Chameleon maintains awareness of the structure of the application it is working with.

This allows the AI to reason about:

* Pages
* Components
* Routes
* Project files
* Existing code
* Application architecture

The implementation planner follows a controlled project context instead of simply allowing the AI to invent arbitrary file locations.

This reduces common AI coding problems such as:

* Creating duplicate components
* Modifying nonexistent files
* Using incorrect paths
* Rebuilding existing functionality
* Making unrelated changes

---

###  AI Debugging

Chameleon can analyze development errors and help identify problems in generated applications.

The debugging workflow can provide the AI with relevant project information and error output so it can determine what needs to be fixed.

This is particularly useful for problems such as:

* TypeScript errors
* React errors
* Missing imports
* Invalid component usage
* Incorrect file references
* Build errors
* Generated code problems

---

###  Implementation Plans

Before modifying a project, Chameleon can generate a structured implementation plan.

A plan describes the intended changes rather than immediately changing the source code.

For example:

```json
{
  "tasks": [
    {
      "type": "modify",
      "path": "src/pages/Calculator.tsx",
      "description": "Create the calculator interface and implement calculator interactions."
    },
    {
      "type": "create",
      "path": "src/components/CalculatorButton.tsx",
      "description": "Create a reusable calculator button component."
    }
  ]
}
```

This provides a clear boundary between:

1. Understanding the request
2. Planning the implementation
3. Writing the code
4. Running the application
5. Debugging the result

---

##  How Chameleon Works

A simplified Chameleon workflow looks like this:

```text
                 ┌──────────────┐
                 │     User     │
                 └──────┬───────┘
                        │
                        ▼
                Natural Language
                        │
                        ▼
                 ┌──────────────┐
                 │    Planner   │
                 └──────┬───────┘
                        │
                        ▼
               Implementation Plan
                        │
                        ▼
                 ┌──────────────┐
                 │     Coder    │
                 └──────┬───────┘
                        │
                        ▼
                  Source Code
                        │
                        ▼
                 ┌──────────────┐
                 │     Vite     │
                 │ Dev Server   │
                 └──────┬───────┘
                        │
                        ▼
                 Live Application
                        │
                        ▼
                 ┌──────────────┐
                 │ Visual Editor│
                 └──────┬───────┘
                        │
                        ▼
                  Further Changes
```

Chameleon does not replace the underlying application.

The generated application remains a normal React project containing actual source code that can be opened and modified outside Chameleon.

---

#  Technology

Chameleon is built using modern web and desktop technologies.

### Desktop

* Electron
* Node.js

### Frontend

* React
* TypeScript
* Vite
* HTML
* CSS

### Backend

* Node.js
* Express

### Data

* SQLite for local application data and configuration

### AI

Chameleon supports multiple AI providers, allowing users to choose between local and cloud-based models.

---

#  AI Providers

Chameleon is designed to avoid locking users into a single AI provider.

Depending on the configured provider, you can use different models for planning and code generation.

Supported providers include:

* **Ollama**
* **OpenRouter**
* **OpenAI**
* **Anthropic**

The provider system allows the planning model and coding model to be configured independently.

For example:

```text
Planning Model
      │
      └──> Smaller / faster model

Coding Model
      │
      └──> Larger / code-specialized model
```

This allows users to optimize the balance between speed, quality, hardware requirements, and API costs.

---

#  Local AI with Ollama

Chameleon can work with local models through Ollama.

This allows you to run AI models directly on your own computer without sending your source code to a cloud AI provider.

For example:

```text
Chameleon
    │
    ▼
Ollama
    │
    ▼
Local AI Model
    │
    ▼
Generated Code
```

This can be useful for:

* Privacy-sensitive projects
* Offline development
* Avoiding API costs
* Experimenting with local models
* Using your own hardware

A sufficiently capable computer is recommended when running larger local models.

---

#  API Key Security

Chameleon stores provider configuration locally.

Where supported by the operating system, sensitive credentials can be protected using Electron's secure storage facilities.

**Never commit API keys to Git.**

If you are developing Chameleon from source, keep environment variables and other secrets out of version control.

Example:

```text
.env
*.env
```

should generally be included in `.gitignore`.

---

#  Installation

## Requirements

Before running Chameleon from source, make sure you have:

* Node.js
* npm

For local AI:

* Ollama
* A compatible AI model
* Sufficient RAM/VRAM for the selected model

---

#  Building Chameleon

Chameleon is distributed as a desktop application using Electron.

A production build packages the Electron application together with the required runtime files.

Typical build commands may include:

```bash
npm run build
```

and/or:

```bash
npm run dist
```

depending on the configured Electron build system.

---

#  Project Architecture

A simplified representation of the project looks like:

```text
chameleon/
│
├── client/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   └── ...
│   │
│   └── ...
│
├── server/
│   ├── app.js
│   ├── routes/
│   ├── services/
│   └── ...
│
├── electron/
│   └── ...
│
├── package.json
├── package-lock.json
└── README.md
```

The exact structure may change as Chameleon develops.

---

#  Generated Projects

Chameleon-generated projects are normal application projects.

For example:

```text
MyProject/
│
├── src/
│   ├── components/
│   │   ├── Button.tsx
│   │   └── Card.tsx
│   │
│   ├── pages/
│   │   ├── Home.tsx
│   │   └── Settings.tsx
│   │
│   ├── App.tsx
│   └── main.tsx
│
├── public/
├── package.json
├── tsconfig.json
└── vite.config.ts
```

Chameleon does not require users to learn a proprietary project format.

The objective is to produce maintainable source code that can be used independently.

---

#  Typical Workflow

A typical workflow looks like this:

### 1. Create a project

Start a new React application from Chameleon.

### 2. Describe what you want

For example:

```text
Create a modern dashboard for managing a personal
finance account. Include a sidebar, balance card,
monthly spending chart, recent transactions and
a settings page.
```

### 3. Chameleon analyzes the project

The planner determines:

* Which files already exist
* Which files need to be created
* Which components can be reused
* Which routes need to be modified

### 4. Chameleon generates an implementation plan

The requested changes are converted into structured tasks.

### 5. The coder implements the plan

The coding model writes or modifies the required source files.

### 6. Preview the result

The application is launched and displayed in the preview.

### 7. Iterate

You can continue using natural language:

```text
Make the sidebar collapsible.
```

Then:

```text
Change the transaction table to show
icons and category badges.
```

Then:

```text
Add dark mode.
```

The application can evolve through an iterative conversation rather than a single generation.

---

#  Design Philosophy

Chameleon is built around several principles.

## 1. Natural language should be a development interface

Programming languages are powerful, but they are not always the easiest interface for expressing design intent.

Chameleon allows users to describe the desired result in natural language while still producing real source code.

---

## 2. AI should modify real projects

Chameleon is not intended to generate disposable mockups.

The goal is to produce applications that developers can continue working on manually.

---

## 3. The user should remain in control

AI-generated code should not become a black box.

Users can inspect the generated files and continue development using traditional tools.

---

## 4. Planning matters

Large coding requests become increasingly unreliable when an AI model tries to solve everything in a single response.

Chameleon therefore separates planning and implementation.

---

## 5. Local AI should be a first-class option

Cloud AI is useful, but developers should also have the ability to run models locally.

Chameleon therefore supports Ollama alongside cloud providers.

---

#  Current Status

Chameleon is currently in active development.

The core system is being developed around:

* AI project generation
* AI project modification
* Planner/Coder architecture
* React + TypeScript support
* Live previews
* Visual editing
* Project structure analysis
* AI debugging
* Multiple AI providers
* Local Ollama support
* Cloud model support
* Electron distribution

Some features may still change significantly before a stable release.

---

#  Roadmap

## Coming Soon

* [ ] Improved project generation
* [ ] Improved code modification
* [ ] More reliable AI planning
* [ ] Better TypeScript error handling
* [ ] Improved visual editor
* [ ] Better component detection
* [ ] More robust project context
* [ ] Improved model configuration
* [ ] Better project recovery/versioning
* [ ] More polished onboarding
* [ ] Stable Windows release

## Future

* [ ] Additional frontend frameworks
* [ ] More advanced visual editing
* [ ] Component library integration
* [ ] Advanced AI agents
* [ ] Automated testing
* [ ] Automated debugging
* [ ] Git integration
* [ ] Project version history
* [ ] Plugin/extension system
* [ ] More AI providers
* [ ] More local model support
* [ ] Improved multi-file reasoning
* [ ] Cross-platform releases

The roadmap is subject to change as development progresses.

---

#  Experimental Features

Some Chameleon functionality may be considered experimental while development continues.

Experimental functionality may include:

* Visual source-code editing
* Automatic component detection
* AI debugging
* Automatic project architecture analysis
* Multi-agent workflows
* Automatic code correction

These features may change or be removed without maintaining backwards compatibility.

---

#  Reporting Bugs

Found a bug?

Please report it through the project's GitHub issue tracker.

When reporting an issue, include as much relevant information as possible:

* Operating system
* Chameleon version
* AI provider
* AI model
* Steps to reproduce the problem
* Error messages
* Relevant logs
* Screenshots when useful

A good bug report makes it significantly easier to reproduce and fix the problem.

---

#  Feature Requests

Feature requests are welcome.

When proposing a feature, explain:

1. What problem the feature solves
2. How you expect it to work
3. Why it would be useful
4. Examples of how you would use it

This helps distinguish useful improvements from features that would add unnecessary complexity.

---

#  Development Disclaimer

Chameleon uses AI to generate and modify source code.

AI-generated code can contain:

* Bugs
* Security vulnerabilities
* Incorrect assumptions
* Inefficient implementations
* Invalid dependencies
* Breaking changes

Always review generated code before using it in production.

Chameleon is a development tool, not a guarantee that generated software is correct or secure.

---

#  Privacy

Chameleon can operate using local AI models through Ollama.

When using cloud AI providers, prompts and relevant project context may be sent to the configured provider according to that provider's API and privacy policies.

Users should understand which provider they have configured before working with sensitive source code.

Chameleon itself is designed as a local desktop development environment rather than a hosted application that requires uploading entire projects to a central Chameleon server.

---

#  License

See the [`LICENSE`](LICENSE) file for the complete license text.

---

#  Support the Project

If you find Chameleon useful:

* Star the repository
* Report bugs
* Suggest features
* Share the project with other developers

---

#  Links

* **GitHub:** https://github.com/MrJaki/chameleon-website
* **Issues:** https://github.com/MrJaki/chameleon-website/issues

---

#  Chameleon

**Describe it. Build it. Change it.**

Chameleon is an attempt to make software development more direct by turning natural language into an interface for real application development.

Instead of choosing between a visual editor and a traditional code editor, Chameleon aims to combine both:

```text
Natural Language
       +
   AI Planning
       +
  Source Code
       +
 Visual Editing
       +
  Live Preview
       ↓
   Application
```

The code remains yours.

The project remains yours.

The AI is the tool.
