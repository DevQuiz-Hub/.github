# DevQuiz-Hub 🚀

Welcome to **DevQuiz-Hub**, a centralized ecosystem of interactive self-assessment web applications, designed to consolidate knowledge in Computer Science and technical examinations.

This organization serves as a software laboratory where question banks are completely decoupled from the rendering logic, enabling agile, lightweight deployments with zero external dependencies.

## 🛠️ System Architecture

Each test module within this organization follows a decoupled architecture pattern based on three core components:

1. **Data Layer (`.json`)**: Stores structured questions, semantic metadata by topics, and dynamic configuration rules.
2. **Logic Layer (`quiz.js`)**: An asynchronous Vanilla JavaScript engine (`async/await`) responsible for local API consumption (`fetch`), in-place shuffling, session state management (`Map`), and defensive data normalization against duplicate IDs.
3. **Presentation Layer (`index.html` + CSS Custom Properties)**: A responsive Single Page Application (SPA) user interface featuring a clean, modern CSS variables architecture (`:root`), optimized for performance and readability in dark mode.

---

## 📊 JSON Schema Specification (Data Contract)

The engine strictly processes the following data contract, allowing the injection of any question bank without modifying a single line of code:

```json
{
  "settings": {
    "show_explanation": true,
    "shuffle_questions": true,
    "shuffle_options": true,
    "show_progress": true
  },
  "questions": [
    {
      "id": "string (unique)",
      "type": "single_choice",
      "question": "string",
      "options": ["string"],
      "correct_answer": "string",
      "explanation": "string",
      "meta": {
        "tema": "string",
        "original_question_number": number,
        "correct_letter": "string"
      }
    }
  ]
}
```

## ⚙️ Core Technical Features
* **Efficient Asynchronous Loading**: Local data consumption bypassing cache mechanisms via strict header policies (`cache: 'no-store'`).
* **In-Place Shuffling Algorithm**: Randomized ordering of questions and options without altering the integrity of the correct answer mapping.
* **Robust State Management**: In-memory persistence of user-selected answers utilizing native `Map` structures to enable seamless bi-directional navigation.
* **CI/CD Deployment**: Out-of-the-box support for instant hosting via **GitHub Pages**.
