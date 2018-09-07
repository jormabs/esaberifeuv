<template>
  <div ref="principal" class="principal" :class="usuario.pasaporte ? 'tienePasaporte' : 'noTienePasaporte'"
  @mousemove="mostrarCoordenadas" >
    <div>
      <span>{{titulo}} - <b>{{anio}}</b> - {{x}}, {{y}}</span>
    </div>
    <div>
      <span>
        {{nombreCompleto}}
      </span>
    </div>
    <div>
      <span>
        Edad: {{edadUsuario}}
      </span>
    </div>
    <div>
      <span>
        Email: <input class="texto" type="text" v-model="usuario.email"> {{usuario.email}}
      </span>
    </div>
    <div>
      <span v-once>
        Email Original:
        <b>{{usuario.email}}</b>
      </span>
    </div>
    <div>
      <span>
        ¿Hijos?: <input type="checkbox" v-model="usuario.hijos"> {{tieneHijos}}
      </span>
    </div>
    <div>
      <a :href="usuario.portafolio" target="_blank">Portafolio</a>
    </div>
    <div>
      <span>
        ¿Pasaporte?: <input type="checkbox" v-model="usuario.pasaporte">
      </span>
    </div>
    <div>
      <input class="texto" type="text" v-model="mensaje" @keydown.enter="mostrarMensaje">
    </div>
    <div id="example-3">
      <button @click="cambiarAnio(3)">Cambiar Año</button>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      titulo: 'Lienzos',
      anio: 2018,
      x: 0,
      y: 0,
      mensaje: 'hola',
      usuario: {
        nombres: 'Juan Carlos',
        apellidos: 'López Martinez',
        fechaNacimiento: new Date(1994, 5, 10),
        email: 'carlos@gmail.com',
        hijos: true,
        portafolio: 'https://vuejs.org/',
        pasaporte: true
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
  },
  methods: {
    cambiarAnio(cantidad) {
      this.usuario.pasaporte ? this.anio += cantidad : this.anio -= cantidad
    },
    mostrarCoordenadas(event) {
      this.x = event.clientX - this.$refs.principal.clientLeft
      this.y = event.clientY - this.$refs.principal.clientTop
    },
    mostrarMensaje() {
      console.log(this.mensaje)
    }
  }
}
</script>

<style>
.principal {
  border-color: rgb(169, 196, 255);
  border-width: 10px;
  border-style: solid;
}

.tienePasaporte {
  background-color: darkolivegreen;
}

.noTienePasaporte {
  background-color: brown;
}

div {
  margin: 10px;
  padding: 10px;
  display: block !important;
  box-sizing: border-box !important;
  font-size: 14pt;
}

button {
  background-color: azure;
  margin: 10px;
  padding: 10px;
  font-size: 14pt;
}

.texto {
  border-style: solid;
  border-width: 1px;
  border-color: black;
  margin: 5px;
  height: 24px;
  background-color: white;
}
</style>

