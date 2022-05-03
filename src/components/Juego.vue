<template>
  <div class="container d-flex  align-items-center flex-column">
    <div class="row">
      <div class="col">
        <div class="d-flex justify-content-center align-items-center">

         <img class="imagen" alt="Vue logo" src="../assets/logo.png" />
        <h1>Piedra, papel o Tijera</h1>
        </div>
        <div>

        <button
          @click="playGame"
          class="btn btn-primary btn-lg mt-3"
          :disabled="btnPlay"
        >
          Empezar
        </button>
        </div>
      </div>
    </div>
    <div v-if="btnPlay" class="row">
      <div class="col mt-3">
        <h3>Elige una de las opciones</h3>
        <button class="btn btn-warning" @click="() => opcionPlayer(0)">
          <i class="fa fa-hand-rock-o fa-4x" aria-hidden="true"></i>
        </button>
        <button class="btn btn-info ms-2" @click="() => opcionPlayer(1)">
          <i class="fa fa-hand-paper-o fa-4x" aria-hidden="true"></i>
        </button>
        <button class="btn btn-danger ms-2" @click="() => opcionPlayer(2)">
          <i class="fa fa-hand-scissors-o fa-4x" aria-hidden="true"></i>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      opciones: ["piedra", "papel", "tijera"],
      bot: 0,
      btnPlay: false,
      player: 0,
    };
  },
  methods: {
    opcionBot() {
      this.bot = Math.floor(Math.random() * 3);

    },
    showAlert(valor) {

      let mensaje=`Elegiste ${this.opciones[
            this.player
          ].toUpperCase()} y el bot eligió ${this.opciones[
            this.bot
          ].toUpperCase()}`
     
      if (valor === "win") {
        this.$swal({
          icon: "success",
          title: "GANASTE!!",
          text: mensaje ,
        });
      } 
      if (valor==="empate") {
        this.$swal({
          icon: "info",
          title: "EMPATE",
          text: mensaje,
        });
      } 
      if(valor==='loser') {
        this.$swal({
          icon: "error",
          title: "PERDISTE!",
          text: mensaje,
        });
      }
    },
    opcionPlayer(opcion) {
      this.player = opcion;
      switch (true) {
        case this.player === 0 && this.bot === 2:
          this.showAlert("win");

          this.btnPlay = false;

          break;
        case this.player === 1 && this.bot === 0:
          this.showAlert("win");
          this.btnPlay = false;

          break;
        case this.player === 2 && this.bot === 1:
          this.showAlert("win");
          this.btnPlay = false;

          break;
        case this.player === this.bot:
          this.showAlert("empate");

          this.btnPlay = false;

          break;

        default:
          this.showAlert("loser");
          this.btnPlay = false;
          break;
      }
      
    },
    playGame() {
      
      this.btnPlay = true;
      this.opcionBot();
    },
  },
};
</script>

<style scoped>
.container{
  height: 100vh;
}
.imagen{
  width: 50px;
}

</style>
