<template>
  <div class="continer">
    <h2>Digital Clock</h2>
    <div class="clock">{{ time }}</div>
    <div class="date">{{ date }}</div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const time = ref('')
const date=ref('')

let interval 

function updateClock() 
{
  const now = new Date()
time.value = now.toLocaleTimeString()
date.value = now.toLocaleDateString('en-GB',
{ weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' }) 

}

onMounted(()=>{
  updateClock()
  interval=setInterval(updateClock , 1000)
})

onUnmounted(() => {
  clearInterval(interval)

})




</script>

<style>
body {
  margin: 0;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: Arial, sans-serif;

  background: linear-gradient(135deg, #89c8ff, #1e3a5f);
}

.continer {
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
}

h2 {
  color: white;
  font-size: 40px;
  text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.3);
  margin-bottom: 20px;
  text-align: center;
}

.clock {
  padding: 25px 60px;

  font-size: 50px;
  font-weight: bold;
  color: white;

  background: rgba(255, 255, 255, 0.15);

  border-radius: 20px;

  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);

  backdrop-filter: blur(8px);

  min-width: 280px;
}
.date {
  padding: 25px 60px;
  margin: 20px;
  font-size: 50px;
  font-weight: bold;
  color: white;

  background: rgba(255, 255, 255, 0.15);

  border-radius: 20px;

  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);

  backdrop-filter: blur(8px);

  min-width: 280px;
}

</style>
