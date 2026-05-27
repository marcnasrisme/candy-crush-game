# Candy Crush

A complete match-3 game in a single HTML file. Open `index.html` in any modern browser — no build step, no dependencies, no install.

~1400 lines of vanilla HTML/CSS/JS implementing the full Candy Crush loop: grid generation with no pre-existing matches, swap-and-validate input, cascading clears, gravity refill, score tracking, and animated visual feedback.

## Why this exists

It's a small project but a fun one — the constraint of "everything in one file, no dependencies" forced clean separation of:

- **Grid model** — 2D array of candy types, immutable swap-then-validate semantics
- **Match detection** — horizontal and vertical scan with run-length accumulation
- **Cascade resolver** — clear → gravity → refill loop that runs until the board is stable
- **Animation queue** — coordinated CSS transitions so cascades feel natural, not instant

## How to play

Open `index.html` in a browser. Click two adjacent candies to swap them. If the swap creates a match of 3+, the matched candies clear, the column above falls, new candies drop in, and any new matches cascade automatically. Score accumulates per cleared candy.

Touch input works too — designed mobile-first with `user-scalable=no` and `-webkit-tap-highlight-color: transparent`.

## Tech

- Pure HTML/CSS/JS, no build tools, no frameworks
- CSS gradients + backdrop blur for the glassmorphic look
- CSS keyframe animations for the floating background orbs and title pulse
- Touch-friendly (responsive sizing with `clamp()`)
