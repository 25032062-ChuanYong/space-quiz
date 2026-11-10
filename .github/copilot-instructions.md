# Copilot instructions

## Project overview

This is a dependency-free browser quiz implemented entirely in `index.html`. The file contains the semantic HTML shell, all CSS, the 10-question data set, quiz state, event handlers, scoring, feedback, theme switching, confetti, and results rendering. There is no server, package manager, build system, or separate source directory.

The page has three main UI areas:

- The top bar contains the Orbit Quest brand and the light/dark theme toggle.
- The hero panel provides the mission-control styled heading and decorative space background.
- The quiz card renders either the active question flow or the final results view.

Quiz state is held in the script-level `current`, `score`, and `answered` variables. `renderQuestion()` rebuilds the current answer buttons from the `questions` array; `selectAnswer()` locks the question, marks correct/incorrect answers, updates the score, and enables the next button; `showResults()` replaces the quiz view with the score summary; `resetQuiz()` returns to question one. Keep these transitions consistent when changing the UI.

## Commands and validation

There are no build, test, or lint commands configured. Do not add a package install or build step for routine changes.

For manual browser validation, open the local file directly:

```text
file:///C:/Republic%20Polytechnic/AY2026%20Semester%202/C334%20Agentic%20AI%20Systems/C334%20Worksheets/Lesson%207/space-quiz/index.html
```

Exercise the page in a browser after behavior changes:

1. Use Tab to move through the theme toggle, answer buttons, and next/restart controls.
2. Select both a correct and incorrect answer and verify feedback, answer locking, and score behavior.
3. Advance through all 10 questions and verify the results text and percentage.
4. Use “Launch again” and verify the question and score reset.
5. Toggle both themes and check readability, including the mission-control heading and decorative background.

When using the integrated browser, reload the file after edits and prefer DOM/page inspection for state assertions plus a screenshot for visual changes.

## Code conventions

- Keep the application self-contained in `index.html`; avoid introducing frameworks, external assets, or runtime dependencies unless the project scope explicitly changes.
- Store quiz content as objects in the `questions` array with `question`, `answers`, `correct`, and `fact` fields. `correct` is a zero-based answer index.
- Use the existing `$()` helper and stable element IDs for script-to-DOM references. Dynamically generated answer buttons use `data-index`.
- Preserve native `<button>` controls and the existing `aria-live`, `role="status"`, and `aria-label` attributes. Feedback must remain available to screen readers.
- Keep answer selection single-use: `answered` prevents duplicate scoring, and selected answers disable all answer buttons until the next question.
- Theme state is controlled by `data-theme="dark"` on the root element. Theme-specific colors belong in the CSS custom properties and `[data-theme="dark"]` selectors.
- Keep visual effects decorative and non-interactive. Existing confetti is created and removed by `sprinkle()`; respect the existing `prefers-reduced-motion` media query when adding animation.
- Follow the current style: CSS custom properties for colors, inline event listeners in the existing script, two-space indentation, and double-quoted JavaScript strings.
