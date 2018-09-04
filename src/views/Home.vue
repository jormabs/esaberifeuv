<template>
  <div class="fondo-home">
    <span>Hola, este es el componente Home.vue</span>
    <Hijo />
  </div>
</template>

<script>

import Hijo from '@/components/Hijo.vue'

export default {
  components: {
    Hijo: Hijo
  }
}
</script>


<style>
.fondo-home {
  background-color: rgb(250, 199, 31);
  margin: 20px;
  padding: 20px;
  font-size: 18pt;
}
</style>

