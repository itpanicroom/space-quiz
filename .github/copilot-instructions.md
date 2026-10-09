# Project rules

- Keep this project as a single, self-contained `index.html`; do not add a server, build step, or external dependency.
- Preserve the responsive layout, accessible keyboard interactions, and light/dark theme support.
- Respect `prefers-reduced-motion` for every animation.
- Keep changes focused, and verify behavior in the browser when changing the quiz.

## Build, test, and run

- There is no build, dependency-install, automated test, or lint command configured; the app runs directly from the HTML file.
- On macOS, run `open index.html` to open it in the default browser. Verify quiz changes there, including keyboard navigation and the results/restart flow.

## Architecture

- `index.html` is the entire application: its `<style>` block contains layout, theme, feedback, and animation rules; its inline script owns question data and quiz behavior.
- The `Q` array is the quiz source of truth. Each entry contains a prompt, four answer choices, the zero-based correct-choice index, and an explanation.
- The script tracks the current question, score, and answer lock. `render()` displays a question, `answer()` records and explains a response, and `finish()` shows results and supports restarting. There is no server or persisted quiz state.

## Project conventions

- Keep all UI, styling, data, and behavior in `index.html`; do not introduce package manifests, external assets, or build tooling.
- Use the existing CSS custom properties and `prefers-color-scheme` rules for theme-aware colors. Keep the layout responsive within the centered quiz card.
- Keep choices as native buttons, preserve visible keyboard focus and the 1–4 answer shortcuts, and keep progress-bar ARIA values synchronized with the visible progress.
- Every animation must be disabled by the existing `prefers-reduced-motion` rule; hide decorative confetti for reduced-motion users.
