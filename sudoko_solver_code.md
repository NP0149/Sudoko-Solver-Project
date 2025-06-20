```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Sudoku Solver</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      display: flex;
      flex-direction: column;
      align-items: center;
      margin-top: 30px;
    }

    table {
      border-collapse: collapse;
    }

    td {
      padding: 0;
    }

    input {
      width: 40px;
      height: 40px;
      font-size: 18px;
      text-align: center;
      border: 1px solid #999;
      box-sizing: border-box;
    }

    /* Bold vertical borders every 3rd column */
    tr td:nth-child(3) input,
    tr td:nth-child(6) input {
      border-right: 3px solid black;
    }

    /* Bold horizontal borders every 3rd row */
    tr:nth-child(3) td input,
    tr:nth-child(6) td input {
      border-bottom: 3px solid black;
    }

    .buttons {
      margin-top: 20px;
    }

    button {
      padding: 10px 20px;
      font-size: 16px;
      margin: 0 10px;
      cursor: pointer;
    }
  </style>
</head>
<body>

  <h2>Sudoku Solver</h2>
  <table id="sudoku"></table>

  <div class="buttons">
    <button onclick="solveSudoku()">Solve</button>
    <button onclick="clearSudoku()">Clear</button>
  </div>

  <script>
    // Create Sudoku Grid
    const table = document.getElementById('sudoku');
    for (let i = 0; i < 9; i++) {
      const row = document.createElement('tr');
      for (let j = 0; j < 9; j++) {
        const cell = document.createElement('td');
        const input = document.createElement('input');
        input.type = 'text';
        input.maxLength = 1;
        cell.appendChild(input);
        row.appendChild(cell);
      }
      table.appendChild(row);
    }

    function getBoard() {
      const board = [];
      const rows = table.querySelectorAll('tr');
      rows.forEach(row => {
        const rowData = [];
        row.querySelectorAll('input').forEach(input => {
          const val = input.value;
          rowData.push(val === "" ? 0 : parseInt(val));
        });
        board.push(rowData);
      });
      return board;
    }

    function setBoard(board) {
      const rows = table.querySelectorAll('tr');
      for (let i = 0; i < 9; i++) {
        const inputs = rows[i].querySelectorAll('input');
        for (let j = 0; j < 9; j++) {
          inputs[j].value = board[i][j] !== 0 ? board[i][j] : "";
        }
      }
    }

    function isSafe(board, row, col, num) {
      for (let x = 0; x < 9; x++) {
        if (board[row][x] === num || board[x][col] === num) return false;
        const boxRow = 3 * Math.floor(row / 3) + Math.floor(x / 3);
        const boxCol = 3 * Math.floor(col / 3) + x % 3;
        if (board[boxRow][boxCol] === num) return false;
      }
      return true;
    }

    function solve(board) {
      for (let row = 0; row < 9; row++) {
        for (let col = 0; col < 9; col++) {
          if (board[row][col] === 0) {
            for (let num = 1; num <= 9; num++) {
              if (isSafe(board, row, col, num)) {
                board[row][col] = num;
                if (solve(board)) return true;
                board[row][col] = 0;
              }
            }
            return false;
          }
        }
      }
      return true;
    }

    function solveSudoku() {
      const board = getBoard();
      if (solve(board)) {
        setBoard(board);
        alert("Solved!");
      } else {
        alert("No solution exists.");
      }
    }

    function clearSudoku() {
      const inputs = table.querySelectorAll('input');
      inputs.forEach(input => input.value = '');
    }
  </script>

</body>
</html>

```
