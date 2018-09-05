<template>
  <v-app>
    <span>{{titulo}} - {{anio}}</span>
    <br>
    <div>
      <span>
        {{nombreCompleto}}
      </span>
      <br>
      <span>
        Edad: {{edadUsuario}}
      </span>
      <br>
      <span>
        Email: <input class="texto" type="text" v-model="usuario.email"> {{usuario.email}}
      </span>
      <br>
      <span>
        ¿Hijos?: <input type="checkbox" v-model="usuario.hijos"> {{tieneHijos}}
      </span>
    </div>
  </v-app>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      titulo: 'Lienzos',
      anio: 2018,
      usuario: {
        nombres: 'Juan Carlos',
        apellidos: 'López Martinez',
        fechaNacimiento: new Date(1994, 5, 10),
        email: '',
        hijos: true
      }
    }
  },
  computed: {
    nombreCompleto() {
      return this.usuario.nombres + ' ' + this.usuario.apellidos
    },
    edadUsuario() {
       let fechaActual = new Date()
       var diferencia = fechaActual - this.usuario.fechaNacimiento
       return Math.floor(diferencia / (1000 * 60 * 60 * 24 * 365.25))
    },
    tieneHijos() {
      return this.usuario.hijos ? 'Sí' : 'No'
    }
  }
}
</script>

<style>
.texto {
  border-style: solid;
  border-width: 1px;
  border-color: black;
  margin: 5px;
}
</style>

