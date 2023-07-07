<template>
  <div>
    <h1>
       UAS PBK A
    </h1>
    <cuaca-widget></cuaca-widget>
    <lokasi-widget></lokasi-widget>
    <stopwatch-widget></stopwatch-widget>
    <tic-tac-toe-widget></tic-tac-toe-widget>
    <foto-widget></foto-widget>
  </div>
</template>

<script>
import CuacaWidget from './components/CuacaWidget.vue'
import LokasiWidget from './components/LokasiWidget.vue'
import StopwatchWidget from './components/StopwatchWidget.vue'
import TicTacToeWidget from './components/TicTacToeWidget.vue'
import FotoWidget from './components/FotoWidget.vue'

export default {
  components: {
    CuacaWidget,
    LokasiWidget,
    StopwatchWidget,
    TicTacToeWidget,
    FotoWidget
  }
}
</script>

<style>
body {
  background-image: url('/src/assets/Lokasi.jpg'); /* Ganti dengan URL gambar yang Anda inginkan */
  background-size: cover;
  background-repeat: no-repeat;

  background-color: #f0f0f0; /* Ganti dengan warna yang Anda inginkan */
}
</style>
<style>
.cuaca-widget {
  background-color: #50cafa; /* Ganti dengan warna yang Anda inginkan */
}
</style>

<style>
.tictactoe-widget {
  background-color: #641717; /* Ganti dengan warna yang Anda inginkan */
}
</style>

