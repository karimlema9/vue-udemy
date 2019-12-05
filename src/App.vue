<template>
  <div id="app" class="principal">
    <span>{{ titulo }}</span>
    <entrada/>
  </div>
</template>

<script>
import Entrada from '@/views/Entrada.vue'

export default {
  name: 'App',
  components: { 
    Entrada
  },
  data() {
    return {
      titulo: 'Entradas'
    }
  }
}
</script>

<style>

html {
  font-size: 62.5% !important;
}

.principal {
  background-color: #FF4C3A;
  padding: 10px;
  border-radius: 5px;
  color: white;
  width: 400px;
  font-size: 3rem;
  text-align: center;
}

a {
    text-decoration: none;
    color: #553f75;
}

button {
  background-color: #FF4C3A;
  color: white;
  font-size: 2.4rem;
  font-weight: bold;
  border-style: none;
  border-radius: 5px;
  padding: 3px 10px;
  margin: 3px 5px;
  min-width: 35px;
  cursor: pointer;
}

input[type='text'] {
  border-radius: 5px;
  font-size: 2.4rem;
  width: 100%;
  line-height: 4rem;
  padding: 3px;
}

</style>