<template>
  <div v-if="btnPlay" class="row">
    <div class="col mt-3">
      <h3>Elige una de las opciones</h3>
      <button class="btn btn-warning" @click="() => funcion(0)">
        <i class="fa fa-hand-rock-o fa-4x" aria-hidden="true"></i>
      </button>
      <button class="btn btn-info ms-2" @click="() => funcion(1)">
        <i class="fa fa-hand-paper-o fa-4x" aria-hidden="true"></i>
      </button>
      <button class="btn btn-danger ms-2" @click="() => funcion(2)">
        <i class="fa fa-hand-scissors-o fa-4x" aria-hidden="true"></i>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    btnPlay: Boolean,
    funcion: Function,
  },
};
</script>

<style></style>
