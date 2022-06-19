<template>
  <div class="dice_container">
    <img
      :class="'die_img ' + `${die.locked}`"
      :src="require(`~/assets/img/dice/${die.value}.svg`)"
      alt=""
      v-for="die in this.dice"
      :key="`${die.id}`"
      :value="`${die.value}`"
      :id="`${die.id}`"
      :name="`${die.name}`"
      @click="toggleDieToLock"
    />
  </div>
</template>


<script>
export default {
  name: "Die",
  props: {
    dice: Array,
  },
  data() {
    return {};
  },
  methods: {
    // ajouter un dés au tableau des dés à conserver (ne pas relancer)
    toggleDieToLock(e) {
      let dieId = e.target.getAttribute("id");
      if (this.counterOfRoll === 3) {
        return;
      } else {
        this.dice[dieId].locked = !this.dice[dieId].locked;
      }
    },
  },
};
</script>

 <style lang="scss" >
@media screen and(max-width:720px) {
  .die_container {
    display: flex;
    width: 100%;
    background-color: rgb(203, 202, 202);
    height: 150px;
  }
  .die {
    width: 20%;
    margin: 16px;
    background-color: grey;
    min-height: auto;
  }
}
</style> 
