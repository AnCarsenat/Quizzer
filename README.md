# Interactive Quiz Platform

A modern, flexible, and user-friendly quiz web application designed for Bac de Français preparation (and general use).

## Features

- **Multiple question types**: Multiple choice, Checkbox, Text (with acceptable answers pool), Number, Select
- **Auto-save progress** — answers are saved automatically and restored on reload
- **Inline feedback** with color coding (like françaisfacile)
- **Spoiler mode** for correct answers
- **Settings panel** with live updates (Dark mode, Randomize, etc.)
- **Multiple quiz support** via URL parameter (`?quiz=...`)
- **Custom quiz loading** from file dialog
- **Resubmit button** (shows feedback again without losing answers)
- **Toast notifications** (no annoying popups)
- **Responsive & clean design**

## Project Structure
```

quizzer/
├── index.html
├── bac2026.json
├── default.json
├── math.json
└── quizs/ ← Recommended folder for organization
├── bac2026.json
├── romantisme.json
└── ...

````

## How to Use

### 1. Start the server (Important!)

```bash
# In the quizzer folder
python -m http.server 8000
````

Then open: http://localhost:8000/index.html

### 2. Loading Quizzes

- Default: `http://localhost:8000/index.html`
- Specific quiz: `http://localhost:8000/index.html?quiz=bac2026`
- The app tries both `./bac2026.json` and `./quizs/bac2026.json`

### 3. Load your own quiz

Click **"📁 Load Custom Quiz"** and select any `.json` file.

## Making your own quizz
### Questions JSON Format

Each question must follow this structure:

```json
{
  "question": "Your question text here?",
  "type": "select | multiple-choice | checkbox | text | number",
  "options": ["Option 1", "Option 2"], // for select, multiple-choice, checkbox
  "correctAnswer": "Exact correct value", // string or number
  "acceptableAnswers": ["15", "fifteen"] // for text type (tolerance)
}
```

### Support for Quiz Metadata

You can now add optional fields at the root of your JSON:

```json
{
  "title": "Mouvements Littéraires - Bac 2026",
  "desc": "Quiz complet couvrant le Classicisme, Romantisme, Réalisme, Symbolisme...",
}
```

### Full Example (bac2026.json)

See the file you already have — it contains a complete Bac de Français 2026 preparation quiz on literary movements.

Extracted sample :
```json
[
  {
  "title": "Mouvements Littéraires - Bac 2026",
  "desc": "Quiz complet couvrant le Classicisme, Romantisme, Réalisme, Symbolisme...",
  },
  {
    "question": "Quel mouvement littéraire est principalement associé à la glorification de la raison, de l'ordre et de la règle classique au XVIIe siècle ?",
    "type": "select",
    "options": ["Humanisme", "Classicism", "Romantisme", "Lumières"],
    "correctAnswer": "Classicism"
  },
  {
    "question": "Qui est considéré comme le théoricien principal du Classicisme avec son Art poétique ?",
    "type": "text",
    "acceptableAnswers": ["Boileau", "Nicolas Boileau"]
  }
]
```

## Supported Question Types

| Type              | Input         | Scoring                          |
| ----------------- | ------------- | -------------------------------- |
| `multiple-choice` | Radio buttons | Exact match                      |
| `checkbox`        | Multi-select  | All correct must be selected     |
| `text`            | Text input    | Any value in `acceptableAnswers` |
| `number`          | Number input  | Numerical equality               |
| `select`          | Dropdown      | Exact match                      |

## Settings

- **Show correct answers**: Under each question or only at the end
- **Use spoiler**: Click to reveal correct answers
- **Randomize questions**
- **Dark mode**

## Keyboard / UX Tips

- Answers are **auto-saved** instantly
- Use **Resubmit** to see feedback again without clearing answers
- Progress is saved per quiz

## Future Improvements (Ideas)

- Timer
- Export results
- Question explanations field
- Score history
- Print mode
- Allow users to make their own quizzes and upload them to the archives
- Allow for embedded adding images
- Allow for embedded markdown

---

**Author**: Grok (xAI)  
**Last Updated**: June 2026
*Not removing above note because code agent worked well*

---
