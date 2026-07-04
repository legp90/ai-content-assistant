# ⚡ AI Assistant Lab

A premium interactive environment and technical content laboratory engineered with **React, TypeScript, and Tailwind CSS**. This application was designed to simulate a production-ready engineering workspace, allowing users to structure prompts and seamlessly manage generation history within a modern, high-fidelity UI optimized for developers.

🌐 **Live Demo:** [View Live Instance](https://ai-content-assistant-alpha.vercel.app/)

---

## 🚀 Key Features

* **Premium UI Design:** A high-scannability dark interface (Zinc-950) built with Tailwind CSS, optimized for long development sessions.
* **Strict Typing with TypeScript:** A robust data architecture utilizing strict interfaces to manage conversation history (`HistoryItem`) and application states.
* **History Sidebar:** Dynamic state management in React to store, list, and retrieve previous queries with real-time timestamps.
* **One-Click Fast Copy:** An interactive button integrated with the browser's Clipboard API to instantly extract the generated output.
* **Connection Resilience (Fallback Architecture):** An intelligent contingency system that simulates technical core responses if external API quotas are exceeded, ensuring a 100% interactive environment.

---

## 🛠️ Tech Stack

* **Frontend:** React (Functional Components & State Hooks)
* **Language:** TypeScript (Strict Mode)
* **Styling:** Tailwind CSS (Utility-First Architecture & Pulse Animations)
* **Build Tool:** Vite (Ultra-fast development environment)
* **Deployment:** Vercel (Automated cloud-linked CI/CD)

---

## 🧠 Highlighted Architecture: The Fallback Engine

One of the most used implementations in this project is its resilience against external service failures (such as regional quota blocks or API Key limits in Google AI Studio):

```typescript
// Fragment of the implemented contingency logic
try {
  const response = await fetch(`[https://generativelanguage.googleapis.com/](https://generativelanguage.googleapis.com/)...`);
  if (!response.ok) throw new Error('Quota Exceeded');
  // ...real data processing
} catch (error) {
  console.warn('Activating backup engine due to Google API quota limit.');
  const simulatedText = generateLocalResponse(prompt);
  setAiResponse(simulatedText);
  setEngineMode('Simulated Core');
}
```

---

## 🔧 Installation and Local Setup

Follow these steps to run the application locally:

1. **Clone the repository:**
   ```bash
   git clone https://github.com/legp90/ai-content-assistant.git
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Start the development server:**
   ```bash
   npm run dev
   ```