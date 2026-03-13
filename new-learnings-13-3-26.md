
### 1. The Document Object Model (DOM)
*   **What we did:** We used `document.getElementById` and `addEventListener` to make the button click change the theme.
*   **The Interview Concept:** The DOM is a tree structure that represents your HTML. JavaScript doesn't "know" about your screen pixels; it interacts with this tree. When you ask "How do I make a button do something?", the answer is almost always: Select the node from the tree, and attach an event listener to it.

### 2. Local Storage (Client-Side Persistence)
*   **What we did:** We added `localStorage.setItem('theme', ...)` so the browser remembers your choice even after a refresh.
*   **The Interview Concept:** The web is "stateless" by default. If you reload, variables reset. `localStorage` is a key-value store in the browser (5-10MB limit) used to persist simple user preferences without needing a database. *Interview Tip:* Know the difference between `localStorage` (persists forever) and `sessionStorage` (clears when the tab closes).

### 3. CSS Specificity and the Cascade
*   **What we did:** Initially, we used custom CSS variables (`--bg-color`) inside a `[data-theme='dark']` selector to override the default `:root` variables.
*   **The Interview Concept:** CSS stands for *Cascading* Style Sheets. Rules "cascade" down. If two rules compete, the more "specific" one wins. By using an attribute selector like `[data-theme='dark']`, we created a rule specific enough to override the defaults.

### 4. Utility-First CSS (Tailwind) vs. Semantic CSS
*   **What we did:** We moved from writing custom CSS (like `.toggle-container { position: absolute }`) to Tailwind classes (`absolute top-5 right-5`).
*   **The Interview Concept:**
    *   **Semantic CSS:** You name classes based on *what they are* (`.navbar`, `.hero-button`).
    *   **Utility CSS:** You name classes based on *what they do* (`.flex`, `.text-center`).
    *   *Why Tailwind?* It reduces the file size of your final CSS bundle and prevents "dead code" (CSS styles you wrote years ago and are afraid to delete).

### 5. Responsive Design (Mobile-First)
*   **What we did:** We used classes like `hidden lg:flex`.
*   **The Interview Concept:** "Mobile-First" means designing for the smallest screen first, then adding complexity for larger screens. In Tailwind, `flex` applies to all screens (mobile default), and `lg:flex` applies *only* when the screen is Large (Desktop). This prevents the common mistake of squishing a desktop layout onto a phone.

### 6. SVGs vs. Image Files
*   **What we did:** We replaced `.png` files with `<svg>` code directly in the HTML.
*   **The Interview Concept:** Bitmaps (PNG/JPG) are made of pixels and get blurry when zoomed. SVGs (Scalable Vector Graphics) are math instructions (`<line>`, `<circle>`).
    *   *Critical benefit:* We used `stroke="currentColor"`. This allowed the icon to instantly change color (white to black) based on the text color of the parent button, which is impossible with a PNG.

### 7. Accessibility (a11y)
*   **What we did:** You'll notice classes like `sr-only` (Screen Reader Only) on generic text inside the buttons.
*   **The Interview Concept:** Not everyone sees your website. Blind users use Screen Readers that read code aloud. An icon button means nothing to them. `sr-only` hides text visually but keeps it in the DOM for screen readers to say "Toggle Theme" instead of just silence or "Button".

### 8. Git and Version Control
*   **What we did:** We created a `.gitignore` file to exclude `.DS_Store`.
*   **The Interview Concept:** Git tracks changes, but you don't want to track *everything*. System files (`.DS_Store`), dependencies (`node_modules`), and API keys should never be committed. "Polluting the repo" with these files is a common junior mistake.

### 9. Semantic HTML
*   **What we did:** We used `<nav>`, `<header>`, and `<button>` instead of just wrapping everything in `<div>` tags.
*   **The Interview Concept:** `<div>` implies nothing. `<button>` implies interactivity (and gives you free keyboard support, like hitting 'Enter' to click). Using semantic tags helps Search Engines (SEO) understand your page structure and helps accessibility tools navigate.

### 10. Script Loading and CDNs
*   **What we did:** We struggled with `@tailwindcss/browser@4` and switched to `cdn.tailwindcss.com` (v3).
*   **The Interview Concept:** A CDN (Content Delivery Network) hosts files on servers all over the world so they load faster for users.
    *   *The Bug:* Different versions of libraries often have breaking changes (API differences). In v4, configuration happens in CSS; in v3, it happens in JS. Recognizing version mismatch is a key debugging skill.
