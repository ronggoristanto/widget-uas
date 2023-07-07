<template>
  <div>
    <h2>Cuaca Widget</h2>
    <div class="weather-info">
      <p>Lokasi: {{ location }}</p>
      <p>Cuaca: {{ weather }}</p>
      <p>Suhu: {{ temperature }}°C</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      location: 'Jakarta, Indonesia',
      weather: 'Sunny',
      temperature: 25
    }
  }
}
</script>

<style scoped>
.weather-info {
  background-color: #f0f0f0;
  padding: 10px;
  border-radius: 4px;
}
</style>
