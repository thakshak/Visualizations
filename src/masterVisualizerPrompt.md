Act as an Expert Frontend Developer and Computer Science Educator. I want you to write a single-file HTML/CSS/JS web application that interactively visualizes the algorithm to solve this coding problem: 

**Problem:** [Insert LeetCode Link or Problem Description here]
**Visual Metaphor:** [Optional: E.g., "Use 3D bins for workers and blocks for jobs", "Use a binary tree with glowing nodes", "Use a 2D grid like a maze"]

Please build this exactly to the following architectural and layout specifications:

### 1. Layout & UI Structure (Top to Bottom)
*   **Configuration Panel (Top):** Inputs for the user to change the problem variables (e.g., arrays, target numbers). Include an "Apply Setup" button and a "Randomize!" button.
*   **Controls Panel:** Buttons for "Start Learning!", "Pause/Resume", and "Stop & Reset". Include an "Animation Speed" slider (e.g., 100ms to 3000ms).
*   **Teacher's Blackboard (Middle):** A large, visually distinct box that acts as an educator. It must have two text areas:
    *   `Variables`: Shows the raw math/state (e.g., `left=0, right=10, mid=5`).
    *   `Teacher Text`: Explains exactly what the algorithm is doing at that exact moment in simple, plain English (e.g., "Let's check if 5 is the answer... Oh no, it's too small!").
*   **Visualization Area (Bottom):** The visual representation of the arrays, trees, or graphs. 
    *   *Critical CSS:* Give the `body` or this bottom container massive bottom padding (at least `120px`) and `overflow: auto` so mobile browser address bars do not cover the visualization. Use `flex-wrap` for elements so they don't break the page if the user inputs large arrays.

### 2. Execution & Technical Architecture
*   **Single File:** All HTML, CSS, and JS must be in one file. Do not use external libraries (no React, no D3). Use standard DOM manipulation.
*   **The Real Algorithm:** Do not mock the steps. Write the actual algorithm (e.g., DFS, Binary Search, DP) and weave the UI updates directly into the algorithm's logic.
*   **Async/Await Animation:** The algorithm must run inside an `async` function. Create a `sleep(runId)` function that uses `await new Promise(...)` tied to the Speed Slider value to pace the animation.
*   **Pause Logic:** Inside the `sleep()` function, include a `while(isPaused)` loop that checks every 100ms so the user can freeze the algorithm mid-execution.
*   **Safe Resetting (Run ID):** Maintain a global `currentRunId` integer. Increment it every time "Start" or "Reset" is clicked. Pass `runId` into the algorithm and the `sleep` function. After every `await sleep()`, add a check: `if (!isRunning || currentRunId !== runId) return;`. This prevents visual ghosting/glitches if the user clicks reset and restart rapidly.
*   **State Locking:** Disable the config inputs and the "Start" button while the algorithm is running. Re-enable them on completion or reset.

Make the UI look modern, dark-themed, and highly educational. Output the complete code block.
