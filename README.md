# TicTacToe_AI_Minimax
Simple Tic Tac Toe game on 3x3 table with a Minimax algorithm implementation. Using Vanilla Javascript and p5.js for visualization and practise.

#### Source links and others:
https://en.wikipedia.org/wiki/Minimax

https://www.ntu.edu.sg/home/ehchua/programming/java/JavaGame_TicTacToe_AI.html


##### Minimax function:

```javascript
function minimax(board, depth, isMaximizing) {
  let result = checkWinner();
  if (result !== null) {
    return scores[result];
  }

  if (isMaximizing) {
    let bestScore = -Infinity;
    for (let i = 0; i < 3; i++) {
      for (let j = 0; j < 3; j++) {
        // Is the spot available?
        if (board[i][j] == '') {
          board[i][j] = ai;
          let score = minimax(board, depth + 1, false);
          board[i][j] = '';
          bestScore = max(score, bestScore);
        }
      }
    }
    return bestScore;
  } else {
    let bestScore = Infinity;
    for (let i = 0; i < 3; i++) {
      for (let j = 0; j < 3; j++) {
        // Is the spot available?
        if (board[i][j] == '') {
          board[i][j] = human;
          let score = minimax(board, depth + 1, true);
          board[i][j] = '';
          bestScore = min(score, bestScore);
        }
      }
    }
    return bestScore;
  }
}
```
