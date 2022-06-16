<template>
  <div class="gamezone">
    <Scoreboard />
    <div class="dice_container">
      <img
        :class="'die_img ' + die.locked"
        :src="require(`~/assets/img/dice/${die.value}.svg`)"
        alt=""
        v-for="die in dice"
        :key="`${die.id}`"
        :value="`${die.value}`"
        :id="`${die.id}`"
        :name="`${die.name}`"
        @click="toggleDieToLock"
      />
    </div>

    <div className="btn-container" v-if="!gameIsStart">
      <button type="button" @click="startTheGame">Nouvelle partie!</button>
    </div>
    <div className="btn-container" v-else>
      <div>Partie en cours!</div>
      <div className="text">
        RELANCE<span v-if="this.counterOfThrow > 1">S</span> DISPONIBLE<span
          v-if="this.counterOfThrow > 1"
          >S: </span
        ><span>{{ this.counterOfThrow }}</span>

        <button
          type="button"
          class="btn_throw"
          @click="lancerLesDes"
          v-if="counterOfThrow > 0"
        >
          Relancer
        </button>
        <button
          type="button"
          class="btn_throw"
          v-else-if="counterOfThrow === 0"
          disabled
        >
          Fin du tour
        </button>
      </div>
    </div>

    <div>{{ this.counterOfTurn }}</div>
    <div>
      <!-- <span v-for="die in dice" :key="die.id">{{ die.locked }}</span> -->
    </div>
  </div>
</template>

<script>
/* import Die from "~/components/Die.vue"; */
import Scoreboard from "~/components/Scoreboard.vue";

export default {
  components: { /* Die ,*/ Scoreboard },
  name: "IndexPage",
  data() {
    return {
      dice: [
        { id: 0, value: "1", name: "die1", locked: false, roll: false },
        { id: 1, value: "1", name: "die2", locked: false, roll: false },
        { id: 2, value: "1", name: "die3", locked: false, roll: false },
        { id: 3, value: "1", name: "die4", locked: false, roll: false },
        { id: 4, value: "1", name: "die5", locked: false, roll: false },
      ],

      gameIsStart: false,
      counterOfThrow: 3,
      counterOfTurn: 13,
    };
  },

  methods: {
    // lancer la partie
    startTheGame() {
      this.gameIsStart = true;
      console.log(this.gameIsStart);
    },

    // ajouter un dés au tableau des dés à conserver (ne pas relancer)
    toggleDieToLock(e) {
      let dieId = e.target.getAttribute("id");
      console.log(dieId);

      this.dice[dieId].locked = !this.dice[dieId].locked;
    },
    lancerLesDes() {
      // enléve 1 aux lancers disponibles
      this.counterOfThrow--;
      // enléve 1 aux tours dans le jeu
      this.counterOfTurn--;
      if (this.counterOfTurn === 0) {
        console.log("partie terminée");
        console.log("ici");
        return;
      }
      if (this.counterOfThrow === 0) {
        console.log("vous n'avez plus de lancer disponibles");
        console.log("ici");
        return;
      } else {
        // si le dés n'est pas locké dans le tableau, lancer
        this.dice.map((die) => {
          if (!die.locked) {
            die.roll = true;
            die.value = Math.round(Math.random() * (6 - 1) + 1);
            die.roll = false;
          }
        });
      }
    },
    lockedState() {
      this.dice.map((die) => {
        if ((this.dice[die].locked = true)) {
          return " locked";
        } else {
          return "";
        }
      });
    },
  },
};
</script>

<style lang="scss">
.gamezone {
  height: 100%;
  width: 100%;
}
.dice_container {
  display: flex;
  justify-content: center;
  width: 100%;
  height: 160px;
  border: rgb(77, 77, 237) solid 1px;
  border-radius: 5px;
}
.die_img {
  min-width: 15%;
  margin: 15px;
  height: auto;
  &:hover {
    transform: rotate(360deg);
    transition: 2sec;
  }
}

.btn_throw {
  border: none;
  color: white;
  background-color: green;
  border-radius: 5px;
  padding: 10px;
  width: 150px;
}
.true {
  border: 5px solid red;
  /* display: flex;
  align-items: center;
  justify-content: center;
  z-index: 2000; */
}
.roll {
  transform: rotate(360deg);
  transition: 0.5s;
}
</style>


