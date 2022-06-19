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

    <!--  <div class="btn-container" v-if="!gameIsStart">
      <button type="button" @click="startTheGame">Nouvelle partie!</button>
    </div> -->
    <div class="btn-container">
      <div class="text">
        <div>
          RELANCE<span v-if="this.counterOfThrow > 1">S</span> DISPONIBLE<span
            v-if="this.counterOfThrow > 1"
            >S: </span
          ><span>{{ this.counterOfThrow }}</span>
          <div>Nombre de tours restants: {{ this.counterOfTurn }}</div>
        </div>
        <div>
          <button
            type="button"
            class="btn_throw"
            @click="lancerLesDes"
            v-if="counterOfThrow !== 0"
          >
            Lancer les dés
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
        { id: 0, value: 1, name: "first_die", locked: false, roll: false },
        { id: 1, value: 1, name: "second_die", locked: false, roll: false },
        { id: 2, value: 1, name: "third_die", locked: false, roll: false },
        { id: 3, value: 1, name: "fourth_die", locked: false, roll: false },
        { id: 4, value: 1, name: "fifth_die", locked: false, roll: false },
      ],

      gameIsStart: false,
      counterOfThrow: 3,
      counterOfTurn: 12,
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
      if (this.counterOfThrow === 3) {
        return;
      } else {
        this.dice[dieId].locked = !this.dice[dieId].locked;
      }
    },
    lancerLesDes() {
      // enléve 1 aux lancers disponibles

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
            let test = (die.value = Math.round(Math.random() * (6 - 1) + 1));
            console.log(test);
            die.roll = false;
          }
        });
        this.counterOfThrow--;
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
  @media screen and(max-width:680px) {
    display: flex;
    flex-wrap: wrap;
  }
  display: flex;
  justify-content: center;
  width: 80%;
  margin: auto;
  height: 160px;
  border: rgb(77, 77, 237) solid 2px;
  border-radius: 5px;
}
.die_img {
  @media screen and(max-width:680px) {
    margin: 5px;
  }
  max-width: 15%;
  margin: 15px;
  height: auto;
  box-sizing: border-box;
  &:hover {
    transform: rotate(360deg);
    transition: 2sec;
  }
}
.btn-container {
  display: flex;
  justify-content: center;
}
.text {
  display: flex;
  flex-direction: column;

  align-content: center;
  justify-content: center;
  margin: 5px;
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


