# Minesweeper — Java Edition

A fully functional recreation of the classic **Minesweeper** puzzle game built using **Java and Swing**. Features an 8×8 grid, randomized mine placement, recursive tile revealing, and emoji-based visuals — all with zero external dependencies.

---

## Overview

This is a **single-window desktop game** built entirely with Java's standard library. Players uncover tiles on a grid, using numbered clues to deduce the locations of hidden mines. Flag suspects with right-click, and clear every safe tile to win.

All logic runs in-memory, making the app lightweight, fast, and easy to run on any machine with Java installed.

---

## Features

###  Core Gameplay
- Left-click a tile to reveal it
- Right-click to place or remove a 🚩 flag
- Clicking a mine instantly ends the game and reveals all bomb locations
- Clear all non-mine tiles to win

###  Smart Tile Revealing
- Revealed tiles display the count of adjacent mines (1–8)
- Tiles with **zero adjacent mines** recursively flood-fill outward, auto-revealing safe regions
- Numbered hints help deduce mine positions without guessing

###  Win & Loss Detection
- **"Mines Cleared!"** displayed when all safe tiles are uncovered
- **"Game Over!"** displayed on mine detonation with all mines revealed as 💣
- Live mine counter shown in the header throughout the game

###  Emoji-Based UI
- Mines displayed as 💣, flags as 🚩
- Large 70px tiles with bold number fonts for easy readability
- Clean grid layout with no visual clutter

---

## Technologies Used

- Java SE 8+
- Java Swing (`javax.swing`)
- Java AWT (`java.awt`, `java.awt.event`)

---

## Project Structure

```text
├── App.java              # Entry point — instantiates the Minesweeper game
└── Minesweeper.java      # Game board, tile logic, mine placement, and input handling
```

---

## Setup & Usage

1. **Clone the repository:**
   ```bash
   git clone https://github.com/your-username/java-minesweeper.git
   ```
   **OR** download the project as a `.zip` file and extract it.

2. **Compile the source files:**
   ```bash
   javac App.java Minesweeper.java
   ```

3. **Run the game:**
   ```bash
   java App
   ```
---

## Controls

| Input          | Action                              |
|----------------|-------------------------------------|
| Left Click     | Reveal a tile                       |
| Right Click    | Place / remove a 🚩 flag            |

---

## Game Configuration

Default settings defined at the top of `Minesweeper.java`:

| Setting      | Value  | Description                    |
|--------------|--------|--------------------------------|
| `tileSize`   | `70`   | Pixel size of each tile        |
| `numRows`    | `8`    | Number of rows in the grid     |
| `numCols`    | `8`    | Number of columns in the grid  |
| `mineCount`  | `10`   | Total mines placed per game    |

Adjust these values to change board size or difficulty.

---

## Implementation Details

- **`MineTile`** — Custom `JButton` subclass storing each tile's `(row, col)` grid coordinates for event handling
- **Mine Placement** — `setMines()` randomly selects `mineCount` unique tiles at game start using `Random`
- **Recursive Reveal** — `checkMine(r, c)` checks all 8 neighbors; if no adjacent mines are found, it recursively reveals them in a flood-fill pattern
- **Neighbor Counting** — `countMine(r, c)` checks bounds and returns `1` if the target tile is a mine, `0` otherwise; called 8 times per reveal
- **Win Condition** — Tracks `tilesClicked`; when it equals `(numRows × numCols) - mineCount`, the game is won
- **Flag System** — Right-click toggles tile text between `""` and `"🚩"`; flagged tiles are still interactable but cannot be accidentally revealed

---

## Limitations

- No restart button — the window must be closed and re-run to play again
- No timer or score tracking
- Window is fixed size and not resizable
- No difficulty presets (beginner / intermediate / expert)
- First click can land on a mine (no safe-first-click guarantee)

---

## License

This project is **open-source** and intended for **educational and portfolio use**.

---

## Author

Designed and developed by **Zaman Siraj**
