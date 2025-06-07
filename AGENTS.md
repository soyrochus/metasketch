## Software Agent Prompt: Build Metasketch – A Collaborative Vibecoding Application

---

### **General Overview**

Metasketch is both a tool and an experiment designed to test a new workflow pattern called **Vibecoding**. The goal is to create a collaborative environment where analysts—who are not coding experts—work together with AI (via conversational programming and prompt engineering) to design and evolve functional documents, iteratively and visually, alongside technical support. Metasketch connects analysis and development naturally, with a workflow that is both accessible and practical for all team members.

---

### **Project Methodology & User Story**

* **Team Composition:**
  The app is designed for a small team of three to four analysts or functional specialists, supported by one technical consultant (not an architect). Analysts use Vibecoding (conversational, prompt-based programming) to instruct the AI to generate, improve, or correct application artifacts, without directly touching code.
* **Workflow:**
  The team collaborates through short cycles, staying close to a simulated or real stakeholder. The focus is on rapid, iterative delivery—minimizing time from idea to result and allowing continuous feedback and adaptation.
* **Support Role:**
  The technical consultant helps with more complex issues and ensures the outputs meet requirements when the AI alone is insufficient.
* **Experiment Purpose:**
  The primary goal is to validate the Vibecoding approach in real teamwork—not to produce a complex or production-grade app. The journey, collaboration, and learning process are as valuable as the end product.

---

### **What is Metasketch as a Product?**

Metasketch is a collaborative web tool for transforming ideas, requirements, and documentation into living, evolving functional designs. It facilitates a two-phase process:

1. **Functional Document Composition:**

   * Users upload requirements, notes, images, or photos.
   * These become nodes in a visible, editable content tree—the intermediate structure of the final document.
   * Users (analysts) can use a simple Markdown editor to modify, expand, or reorganize texts.
   * The system includes an AI-powered chat or prompt interface for further assistance: reorganizing, summarizing, or modifying content via conversational commands.
   * The process is highly iterative and visual—users see real-time previews and can manually or AI-assist edit content.
2. **Export & Sharing:**

   * Once the design is ready, users export it as a Word or PDF file.
   * The app maintains a “living source” document that can be continuously updated and re-exported.

The UI and interaction model are designed to be intuitive and accessible, so analysts (who may become their own “clients”) can adopt the tool without advanced technical skills. Healthy competition between teams (e.g., multiple teams building their own Metasketch instance) is encouraged to boost commitment and learning.

---

### **UI/UX Specification**

**The main project interface (after login and project selection) is split into four horizontally arranged, resizable panels:**

1. **Documents Panel (far left, minimized by default):**

   * Displays a list of uploaded documents (requirements, notes, images, etc.)
   * Supports uploads and deletions.
   * Designed to use minimal space by default, but can be expanded by the user.
2. **Content Tree Panel (left-center):**

   * Shows a hierarchical, interactive tree of the evolving document structure.
   * Users can add, rename, reorder, or delete nodes.
   * Each node represents a document section or subsection.
3. **Editor Panel (center-right):**

   * Shows a Markdown editor (using CodeMirror or similar) for the currently selected content tree node.
   * Users can edit text manually or via AI suggestions.
   * Real-time preview of Markdown rendering is available.
4. **AI Chat & Instructions Panel (far right):**

   * Features a standard chat interface (user/AI message distinction, persistent history per project).
   * Users can ask the AI to generate, summarize, or reorganize content.
   * The AI responds in context of the current project and content.

* **Panels are resizable via draggable splitters.**
* **Export function:** Users can export the project document as Word or PDF at any time.
* **Modern, clean interface** with user-friendly design and clear feedback on all actions.

---

### **System & Architecture Specification**

* **Backend:**

  * Python with FastAPI as the web backend.
  * Server-side rendering (SSR) via Jinja2 for all HTML pages and templates.
  * HTMX for dynamic UI updates and AJAX (no SPA frameworks like Angular/React).
  * Langchain for AI orchestration, using OpenAI models for conversational, generative, and summarization tasks.
  * If a vector database is needed for semantic search or content retrieval, use Chroma.
  * SQLite for all other data storage (users, projects, content, chat history, etc.).

* **Frontend:**

  * Jinja2-rendered HTML templates.
  * HTMX for dynamic, partial updates and interactivity (e.g., uploading docs, updating content tree, chat).
  * Integrate CodeMirror for the Markdown editor.
  * UI matches the four-panel design described above, clean and uncluttered.

* **Authentication:**

  * Simple username/password authentication (plain text for now, to be improved later).
  * Each user’s data and projects are private and isolated.

* **Data Model:**

  * Users: id, username, password (cleartext), email (optional).
  * Projects: id, user\_id, name, created\_at, updated\_at.
  * Documents: id, project\_id, filename, filetype, upload\_date, blob content.
  * Content Tree Nodes: id, project\_id, parent\_id, title, order, content (Markdown).
  * Chat History: id, project\_id, timestamp, sender (user/AI), message.

* **Project-based Navigation:**

  * After login, users see a list of their projects (with options to create, delete, or select a project).
  * Project selection brings them to the main UI described above.

* **Security & Access:**

  * Each user’s data is private.
  * Simple admin interface (optional) for troubleshooting.

---

### **Implementation Constraints & Priorities**

* Prioritize architectural clarity and onboarding simplicity.
* Do not implement advanced features like multi-user editing or advanced agent orchestration (beyond Langchain/OpenAI).
* Emphasize usability and clarity for non-technical users.
* System must work “out of the box” for analysts unfamiliar with developer tools.
* Clear logging and error feedback for all actions.
* All workflows, content, and interface details must be understandable to non-developers.

---

### **Goal and Evaluation**

The main purpose is to **validate Vibecoding in a realistic team context**. Success is measured by effective collaboration, rapid iteration, and clear demonstration of analysts and AI jointly producing useful, exportable documentation—even if the app is minimal.

---

**Task:**
Generate the full codebase and implementation plan for the described system, using the technologies and architecture above. Ensure that all described features, flows, and constraints are addressed. Deliver a robust, maintainable, and user-friendly collaborative application per the above.

---
