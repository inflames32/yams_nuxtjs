<template>
  <div class="gamezone">
    <Scoreboard :scores="scores" />
    <Die :dice="dice" :counterOfRoll="counterOfRoll" />
    <!--  <div class="btn-container" v-if="!gameIsStart">
      <button type="button" @click="startTheGame">Nouvelle partie!</button>
    </div> -->
    <div class="btn-container">
      <div class="text">
        <Message
          :counterOfRoll="counterOfRoll"
          :counterOfTurn="counterOfTurn"
        />
        <div class="btn_roll_container">
          <button
            type="button"
            class="btn_roll"
            @click="lancerLesDes"
            v-if="counterOfRoll !== 0"
          >
            Lancer les dés
          </button>
          <button
            type="button"
            class="btn_roll"
            v-else-if="counterOfRoll === 0"
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
export default {
  components: {},
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
      scores: [
        { name: "As", score: 1 },
        { name: "Deux", score: 2 },
        { name: "Trois", score: null },
        { name: "Quatre", score: null },
        { name: "Cinq", score: null },
        { name: "Six", score: null },
        { name: "Total", score: null },
        { name: "Bonus>62", score: null },
        { name: "Total+Bonus", score: null },
        { name: "Plus", score: null },
        { name: "Moins", score: null },
        { name: "Total Plus | Moins", score: null },
        { name: "Suite", score: null },
        { name: "Full", score: null },
        { name: "Carré", score: null },
        { name: "Yams", score: null },
        { name: "Total3", score: null },
        { name: "Final", score: null },
      ],

      gameIsStart: false,
      counterOfRoll: 3,
      counterOfTurn: 13,
    };
  },

  computed: {
    test() {
      console.log("computed test");
      let sumAs = this.dice.reduce((total, die) => {
        if (die.value === 1) {
          total + die.value;
        } else {
          total;
        }
        console.log(sumAs);
        return sumAs;
      });
    },
  },

  methods: {
    sumAs() {
      console.log("ici");
      let sumAs = this.dice.reduce((total, die) => {
        if (die.value === 1) {
          total + die.value;
        } else {
          total;
        }
        console.log(sumAs);
        return sumAs;
      });
    },
    // lancer la partie
    startTheGame() {
      this.gameIsStart = true;
      console.log(this.gameIsStart);
    },

    lancerLesDes() {
      // enléve 1 aux tours dans le jeu
      this.counterOfTurn--;
      if (this.counterOfTurn === 0) {
        console.log("partie terminée");
        console.log("ici");
        return;
      }
      if (this.counterOfRoll === 0) {
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
        // enléve 1 aux lancers disponibles
        this.counterOfRoll--;
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
.btn_roll_container {
  display: flex;
  justify-content: center;
  margin: 5px;
}
.btn_roll {
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


