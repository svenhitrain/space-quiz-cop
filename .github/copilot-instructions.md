# Copilot instructions

## Build, test, and lint

- This is a static page with no package manifest, build scripts, automated tests, or lint configuration.
- To run the app, open `index.html` directly in a browser.
- There is no automated single-test command; verify behavior in the browser.

## Architecture

- The app is a single-page quiz implemented entirely in the root `index.html`: semantic markup, embedded CSS, the question bank, and quiz behavior all live there.
- The `questions` array supplies each question, its answer choices, the zero-based `correct` answer index, and the feedback `fact`.
- Quiz state (`current`, `score`, `answered`) drives the intro, question, feedback, and results views. Rendering replaces the contents of `#quiz`; each render function then attaches handlers to the newly created controls.

## Code conventions

- Keep the question data in the existing `questions` array shape and update the displayed question count from `questions.length`.
- Keep styles in the embedded stylesheet and use its CSS custom properties for theme colors. Light/dark colors, small-screen layout, and reduced-motion behavior are already handled there.
- Use native buttons for actions and answers. Preserve accessible names for answer choices, the labeled quiz region and progress bar, live score/feedback updates, and focus movement to question and results headings.
- Mark decorative symbols as `aria-hidden="true"` so they do not pollute screen-reader labels.
