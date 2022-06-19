<template>
  <div class="message">
    <div>
      RELANCE<span v-if="this.counterOfRoll > 1">S</span> DISPONIBLE<span
        v-if="this.counterOfRoll > 1"
        >S : </span
      ><span>{{ this.counterOfRoll }}</span>
    </div>

    <!-- <div>Nombre de tours restants: {{ this.counterOfTurn }}</div> -->
  </div>
</template>

<script>
export default {
  name: "Message",
  props: {
    counterOfTurn: Number,
    counterOfRoll: Number,
  },
};
</script>

<style lang="scss">
.message {
  font-size: 20px;
  margin: 5px;
}
</style>