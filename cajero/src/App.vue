<template>
  <div>
    <div v-if="auth === false">
      <login @enter="validar"/>
    </div>
    <div v-else>
      <cajero :usuarioActivo = usuariosValidado />
    </div>
  </div>
</template>

<script>
import Cajero from './components/Cajero.vue'
import Login from './components/Login.vue'
import { constants } from 'crypto';

export default {
  name: 'app',
  components: {
    Cajero,
    Login
  },
  data() {
    return {
      auth: false,
      usuarios: [],
      usuariosValidado:{}
    }
  },
  mounted() {
    this.cargarUsuarios()
  },
  methods: {
    cargarUsuarios: async function() {
      const data = await fetch( './usuarios.json' )
      this.usuarios = await data.json()
    },
    validar( pass ) {
     console.log('contraseña', pass)
      const cantidadUsuarios = this.usuarios.length
      for( let i = 0; i < cantidadUsuarios ; i++) {

         console.log (this.usuarios[i].pass)
        if (this.usuarios[i].pass == pass) {
          this.usuariosValidado = this.usuarios[i];
          this.auth = true
        }
    }
      
      /* 
      console.log( pass )
      let txt = pass //prompt("Ingrese la clave:");
      if (txt == null || txt == "") {
      } else{
        // let pass = parseInt(user.pass)
        if (parseInt(txt) === 1122) {
          this.auth = true
        }
      } */
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Source+Sans+Pro');
  body {
    margin: 0;

    font-family: "Source Sans Pro", sans-serif;

    background-color: #2a333d;
}
</style>
