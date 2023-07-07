<template>
  <div>
    <h2>Tic-Tac-Toe Widget</h2>
    <div class="board">
      <div class="row" v-for="(row, rowIndex) in board" :key="rowIndex">
        <div class="cell" v-for="(cell, colIndex) in row" :key="colIndex" @click="makeMove(rowIndex, colIndex)">{{ cell }}</div>
      </div>
    </div>
    <button @click="resetBoard">Reset</button>
    <p v-if="gameOver">{{ winner }} wins!</p>
    <p v-else-if="isDraw">It's a draw!</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentPlayer: 'X',
      board: [
        ['', '', ''],
        ['', '', ''],
        ['', '', '']
      ],
      gameOver: false
    }
  },
  methods: {
    makeMove(row, col) {
      if (this.board[row][col] === '' && !this.gameOver) {
        this.board[row][col] = this.currentPlayer;
        this.checkWinCondition();
        this.togglePlayer();
      }
    },
    togglePlayer() {
      this.currentPlayer = this.currentPlayer === 'X' ? 'O' : 'X';
    },
    checkWinCondition() {
      // Check rows
      for (let i = 0; i < 3; i++) {
        if (this.board[i][0] === this.currentPlayer && this.board[i][1] === this.currentPlayer && this.board[i][2] === this.currentPlayer) {
          this.gameOver = true;
          return;
        }
      }
      // Check columns
      for (let i = 0; i < 3; i++) {
        if (this.board[0][i] === this.currentPlayer && this.board[1][i] === this.currentPlayer && this.board[2][i] === this.currentPlayer) {
          this.gameOver = true;
          return;
        }
      }
      // Check diagonals
      if (
        (this.board[0][0] === this.currentPlayer && this.board[1][1] === this.currentPlayer && this.board[2][2] === this.currentPlayer) ||
        (this.board[0][2] === this.currentPlayer && this.board[1][1] === this.currentPlayer && this.board[2][0] === this.currentPlayer)
      ) {
        this.gameOver = true;
        return;
      }
      // Check draw
      if (this.isBoardFull()) {
        this.gameOver = true;
        return;
      }
    },
    resetBoard() {
      this.currentPlayer = 'X';
      this.board = [
        ['', '', ''],
        ['', '', ''],
        ['', '', '']
      ];
      this.gameOver = false;
    },
    isBoardFull() {
      for (let row of this.board) {
        if (row.includes('')) {
          return false;
        }
      }
      return true;
    }
  },
  computed: {
    winner() {
      return this.currentPlayer === 'X' ? 'O' : 'X';
    },
    isDraw() {
      return this.gameOver && !this.winner;
    }
  }
}
</script>

<style scoped>
.board {
  display: flex;
  flex-direction: column;
}

.row {
  display: flex;
}

.cell {
  width: 40px;
  height: 40px;
  border: 1px solid #000;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
}
</style>
