<template>
  <div class="fondo">
    <span class="texto">Hola, este es el componente App.vue</span>
    <Home></Home>
    <Hijo />
  </div>
</template>

<script>
import Home from './views/Home.vue'
import Hijo from '@/components/Hijo'

export default {
  components: {
    Home: Home,
    Hijo: Hijo
  }
}
</script>


<style>

.fondo {
  background-color:darkslategray;
  border-style: solid;
  border-width: 10px;
  border-color:teal;
  padding: 100px;
  width: 800px;
  display: block;
}

.texto {
  color: rgb(226, 226, 226);
  margin: 0 auto;
  display: block;
  width: 600px;
  font-weight: 900;
  text-align: center;
  font-size: 20pt;
}

</style>
