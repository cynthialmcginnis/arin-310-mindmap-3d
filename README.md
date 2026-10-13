# ARIN 310 Course Constellation

An interactive 3D review map for **ARIN 310: Introduction to Artificial Intelligence** at University of Maryland Global Campus (UMGC) Asia.

The map shows all eight units of the course as a constellation. Each unit is a colored star, and its concepts orbit around it. The units rise in course order, with Unit 1 at the bottom and Unit 8 at the top. Lines between colors connect ideas that carry across units. Students open any star to read the concept, write it back in their own words, mark it reviewed, and check themselves with a short quiz.

**Live site:** `https://cynthialmcginnis.github.io/arin-310-mindmap-3d//`

This is a study tool. It is not graded, and it sends no data anywhere.

## What it covers

| Unit | Topic | Concepts |
| --- | --- | --- |
| 1 | Background, Introduction, and Definition of AI | 4 |
| 2 | Machine Learning and Deep Learning | 5 |
| 3 | Natural Language Processing and Generative AI | 7 |
| 4 | Computer Vision and Reinforcement Learning | 8 |
| 5 | Recommender Systems | 7 |
| 6 | Robotics and Robotic Process Automation | 9 |
| 7 | Applications of AI | 7 |
| 8 | The Future of AI | 7 |

That comes to 54 concepts, 24 quiz questions, a 40-term glossary, 29 cross-unit connections, and 6 guided threads.

## Features

- **A 3D map that carries meaning.** Height shows a unit's place in the course. Opening a unit turns its ring of concepts to face you and fades the other units back.
- **Cross-unit connections.** Open a concept and its links to other units light up. The panel explains why each pair connects. For example, it links the 1958 perceptron to neural networks, and RLHF to reinforcement learning.
- **Threads.** Six guided tours follow an idea through the course:
  - When the world changes
  - Fluent is not true
  - You get what you measure
  - From one neuron to language
  - Loops that act
  - Bias in, bias out

  The camera moves stop by stop and draws a numbered route.
- **Active review.** Each concept has an "Explain it back" box and a Mark as reviewed button. Each unit has a three-question quiz with feedback.
- **Progress on the map.** A reviewed concept gets a green ring. The ring around each unit star fills as its concepts are completed.
- **Search and glossary.** Search lights up matching stars. The glossary table can be filtered.
- **A built-in guide.** "How to use" opens on a student's first visit and stays available from the toolbar.
- **Phones and keyboards.** On a phone, the panel becomes a bottom sheet. Every unit and concept can be reached from the unit list and the panel. The arrow keys rotate the map, and the + and − keys zoom.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The whole app: page, styles, script, and course content in one self-contained file |
| `ARIN310_Constellation_LEO_Instructions.html` | Student instructions page with inline styles, ready to paste into LEO (D2L) |
| `README.md` | This file |

The app was delivered as `ARIN310_Course_Constellation.html`. Rename it to `index.html` so GitHub Pages serves it at the repository's root URL.

## Publish on GitHub Pages

1. Create a public repository, for example `arin310-constellation`.
2. Upload `index.html` and this `README.md` to the main branch.
3. Go to **Settings → Pages**.
4. Under **Build and deployment**, set **Source** to **Deploy from a branch**. Choose `main` and `/ (root)`, then select **Save**.
5. Wait a minute or two. The site appears at `https://cynthialmcginnis.github.io/arin310-constellation/`.
6. Paste that URL into the LEO instructions page, replacing `[PASTE THE CONSTELLATION LINK HERE]`. Then update the live site link at the top of this README.

## How student progress works

Progress saves in the student's own browser through `localStorage`, under the key `arin310-review-v1`. This covers reviewed concepts, notes, and quiz answers.

- Nothing is sent to a server or to the instructor.
- Progress does not carry across browsers, devices, or private windows. Clearing browser data erases it.
- Students can select **Export progress** to download a JSON file, and **Import progress** to restore it on another device.
- The key matches the earlier mind map version of this tool, so progress saved there still loads.

## Editing the content

All content lives inside the `<script>` block in `index.html`. No build step is needed: edit the file and upload it again.

| To change | Edit |
| --- | --- |
| Concept text, unit intros, quizzes, glossary | The `DATA` object. Each unit has `title`, `intro`, `concepts` (each with `id`, `title`, and `blocks`), and `quiz` entries in the form `[question, [choices], correct index, explanation]`. |
| Cross-unit connections | The `LINKS` array: `[conceptId, conceptId, reason]` |
| Guided threads | The `THREADS` array: a `title`, a `lede`, and `steps` in the form `[conceptId, note]` |
| Unit colors | The `COLORS` array, one color per unit |
| The How to use guide | The `viewHelp()` function |

Concept IDs follow the pattern `unitIndex-conceptIndex`, counting from zero. For example, `1-2` is Unit 2, concept 3 ("Training, testing, and overfitting").

After editing, open the file in a browser and press F12 to check the console for errors before you upload.

## Technical notes

- It runs on plain HTML, CSS, and JavaScript, drawing the 3D view on a `<canvas>` with its own perspective projection. It uses no frameworks and no 3D library.
- The only external request is to Google Fonts (Bricolage Grotesque, Atkinson Hyperlegible, JetBrains Mono). If the fonts fail to load, the page falls back to system fonts and still works.
- It works in current versions of Chrome, Edge, Firefox, and Safari, on desktop and mobile.
- It respects `prefers-reduced-motion`. When that setting is on, the map turns off auto-rotation and animation.

## Author

Professor Cynthia McGinnis, Associate Professor of Mathematics and Computer Science, UMGC Asia.

Content is adapted from the ARIN 310 course review, *ARIN 310 in Review*.
