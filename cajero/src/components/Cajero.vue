<template>
  <div>
    <div class="header">
      <img class="logo" src="../assets/logo.png" />
      <div class="align-left">
        <span id="nombre">Bienvenido/a {{usuarioActivo.nombre}}</span>
        <img class="avatar" src="../assets/avatar.svg" />
      </div>
    </div>
    <div class="white-container">
      <div class="menu-container">
        <h1 class="tu-cuenta">Tu cuenta</h1>
        <button class="links" @click="extraerDinero()">Extraer dinero</button>
        <button class="links" @click="depositarDinero()">Depositar dinero</button>
        <button class="links" @click="pagarServicio()">Pagar servicios</button>
        <button class="links" @click="transferirDinero()">Transferir dinero</button>
        <button class="links" @click="cambiarLimiteDeExtraccion()">Cambiar límite de extracción</button>
      </div>
      <div class="green-container">
        <div class="cuenta-info">
          <p>Saldo en tu cuenta </p>
          <h3 id="saldo-cuenta">${{usuarioActivo.saldo}}</h3>
          <p id="limite-extraccion">Tu límite de extracción es: {{usuarioActivo.limite}}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["usuarioActivo"],
  name: "Cajero",
  data() {
    return {
      auth: false
    }
  },
  methods: {
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

.avatar {
    display: inline-block;

    vertical-align: text-bottom;
}

.logo {
    display: inline-block;
    width: 200px;
    height: 50px;

    text-align: left;
    vertical-align: text-bottom;
}

.align-left {
    display: flex;
    padding: 8px;

    align-items: center;
}

.tu-cuenta {
    padding-left: 24px;
    margin: 0;
    margin-left: -30px;

    font-family: "Source Sans Pro";
    font-size: 32px;
    font-weight: normal;

    color: #2a333d;
    border-left: 6px solid #2cc197;
}

.header {
    display: flex;
    width: 65%;
    margin: 7% auto 0;
    margin-bottom: 15px;

    justify-content: space-between;
}

.cuenta-info {
    display: block;
    width: 100%;
}

#nombre {
    display: inline-block;
    margin-right: 10px;
    overflow: hidden;

    font-size: 14px;

    text-overflow: ellipsis;

    color: #fff;
}

.links {
    position: relative;

    display: block;
    padding: 0;
    margin: 20px 0;
    margin-bottom: 30px;

    font-family: "Source Sans Pro";
    font-size: 16px;

    cursor: pointer;
    -webkit-transition: all .6s ease-in-out;
       -moz-transition: all .6s ease-in-out;
         -o-transition: all .6s ease-in-out;
            transition: all .6s ease-in-out;
    text-align: left;
    vertical-align: text-bottom;

    color: #666;
    border: 0;
    background-color: transparent;
}

.links:hover {
    margin-left: 10px;

    color: #2cc197;
}

.white-container {
    display: flex;
    width: 65%;
    padding: 30px;
    margin: 0 auto;
    box-sizing: border-box;

    border: 1px solid #979797;
    border-radius: 8px;
    background-color: #fff;

    justify-content: center;
}

.green-container {
    display: flex;
    width: 65%;
    box-sizing: border-box;

    text-align: center;

    color: white;
    border-radius: 8px;
    background-color: #2cc197;

    align-items: center;
}

.menu-container {
    display: block;
    width: 35%;
    padding-right: 20px;
}

.cuenta-container {
    width: 35%;
}

#saldo-cuenta {
    margin-top: 5%;
    margin-bottom: 5%;
    overflow: hidden;

    font-size: 6.5vw;

    text-align: center;
    text-overflow: ellipsis;
}

#limite-extraccion {
    overflow: hidden;

    font-size: 15px;

    text-overflow: ellipsis;
}

@media only screen and (max-width: 800px) {
    .white-container {
        flex-direction: column-reverse;
    }

    .green-container {
        width: 100%;
        margin-bottom: 20px;
    }

    #saldo-cuenta {
        font-size: 8.5vw;
    }

    .menu-container {
        width: 100%;
    }

    .header {
        margin-bottom: 10px;
        flex-direction: column;

        align-items: center;
    }

    .logo {
        margin-bottom: 10px;
    }
}

</style>
