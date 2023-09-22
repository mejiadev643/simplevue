<template>
    <div>
        mi primer componente de vue
        <button @click="increment"> touch me
  {{ count }}
</button>
<h1>{{ poke.gender }}</h1>

<table class="table" v-if="en==1">
  <thead>
    <tr>
      <th scope="col">Gender</th>
      <th scope="col">First Name</th>
      <th scope="col">Last Name</th>
      <th scope="col">Country</th>
      <th scope="col">Picture</th>
    </tr>
  </thead>
  <tbody>
    <tr >
      <td scope="row">{{ poke.gender }}</td>
      <td>{{ poke.name.title + poke.name.first }}</td>
      <td>{{ poke.name.last }}</td>
      <td>{{ poke.location.city }}</td>
      <img :src="poke.picture.medium">
    </tr>
<button type="button" class="btn btn-warning" @click="sincronizar">generar aleatorio</button>
  </tbody>
</table>


</div>
    
</template>

<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios' // node
const count = ref(0)
const poke= ref([])
const en =ref(0)
function increment() {
      // .value is needed in JavaScript
      count.value++
    }
 onMounted(async () => {
  // Coloca aquí el código que deseas ejecutar cuando el componente se monta.
  try {
    const response = await axios.get('https://randomuser.me/api/') // Ejemplo de una solicitud GET a una API
    console.log('Respuesta de la API:', response.data.results[0])
    poke.value=response.data.results[0]
    en.value=1
    // Coloca aquí el código que deseas ejecutar cuando la solicitud sea exitosa
  } catch (error) {
    console.error('Error al realizar la solicitud:', error)
    // Coloca aquí el código que deseas ejecutar en caso de error
  }


})

async function sincronizar(){
    try {
    const response = await axios.get('https://randomuser.me/api/') // Ejemplo de una solicitud GET a una API
    console.log('Respuesta de la API:', response.data.results[0])
    poke.value=response.data.results[0]
    en.value=1
    // Coloca aquí el código que deseas ejecutar cuando la solicitud sea exitosa
  } catch (error) {
    console.error('Error al realizar la solicitud:', error)
    // Coloca aquí el código que deseas ejecutar en caso de error
  }
  }
</script>

<style lang="scss" scoped>


</style>
