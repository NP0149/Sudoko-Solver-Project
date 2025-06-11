

# 🧩 Sudoku Solver

This repository contains a Sudoku Solver that allows users to input Sudoku puzzles and solves them using a backtracking algorithm.

## 🔍 Overview

The Sudoku Solver is a web-based application that lets users:
- Enter a Sudoku puzzle in a 9x9 grid.
- Automatically solve the puzzle using a backtracking algorithm.
- Clear/reset the board for a new puzzle.

## 💻 Technologies Used

- **HTML** – To create the Sudoku grid UI.
- **CSS** – For styling the grid and buttons.
- **JavaScript** – For implementing the solver logic and UI interactions.

## 🚀 Features

- Easy-to-use interface to input puzzle values.
- Instant solve functionality using backtracking.
- Clear button to reset the grid.
- Handles invalid or unsolvable puzzles gracefully.

## 🧠 Algorithm

The core logic is based on the **Backtracking Algorithm**, which works as follows:
1. Try filling in a number from 1 to 9 in an empty cell.
2. Check if it's valid in the current row, column, and 3x3 box.
3. Recursively continue filling in the next cell.
4. If no number is valid, backtrack to the previous cell and try a new number.

## 📁 Folder Structure

├── index.html # HTML file for the UI
├── style.css # CSS file for styling
├── script.js # JavaScript for the solver logic
└── README.md # This file

✍️ Author

Created by [Navya Pasunuri].
📜 License

This project is licensed under the MIT License.
