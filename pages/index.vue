<template>
  <div class="gamezone">
    <Scoreboard />
    <div class="dice_container">
      <img
        class="die_img"
        :src="require(`~/assets/img/dice/${die.value}.svg`)"
        alt=""
        v-for="die in dice"
        :key="`${die.id}`"
        :value="`${die.value}`"
        :id="`${die.id}`"
        :name="`${die.name}`"
        @click="toggleDieToLock"
      />
      <span v-if="lockedState"></span>
    </div>

    <div className="btn-container" v-if="!gameIsStart">
      <button type="button" @click="startTheGame">Nouvelle partie!</button>
    </div>
    <div className="btn-container" v-else>
      <div>Partie en cours!</div>
    </div>

    <div className="text">
      RELANCE<span v-if="this.counterOfThrow > 1">S</span> DISPONIBLE<span
        v-if="this.counterOfThrow > 1"
        >S</span
      >

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
        Plus de relances disponibles
      </button>
    </div>
    <div>{{ this.counterOfThrow }}</div>
    <div>{{ this.counterOfTurn }}</div>
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
        { id: "1", value: "1", name: "die1", locked: false },
        { id: "2", value: "2", name: "die2", locked: false },
        { id: "3", value: "3", name: "die3", locked: false },
        { id: "4", value: "4", name: "die4", locked: false },
        { id: "5", value: "5", name: "die5", locked: false },
        /* { id: "6", value: "5", name: "die6", locked: false },
         { id: "7", value: "5", name: "die7", locked: false },
        { id: "8", value: "5", name: "die8", locked: false }, */
      ],
      dieToLock: [],
      gameIsStart: false,
      counterOfThrow: 100,
      counterOfTurn: 130,
    };
  },
  /*   computed: {
    lockedState() {
      this.dice.map((die) => {
        if ((this.dice[die].locked = true)) {
          return " locked";
        } else {
          return "";
        }
      });
    },
  }, */
  methods: {
    // lancer la partie
    startTheGame() {
      this.gameIsStart = true;
      console.log(this.gameIsStart);
    },

    // ajouter un dés au tableau des dés à conserver (ne pas relancer)
    toggleDieToLock(e) {
      const dieId = e.target.getAttribute("id");
      console.log(dieId);
      console.log("aavnt le click", this.dice[dieId].locked);
      this.dice[dieId].locked = !this.dice[dieId].locked;
      console.log("apres le click", this.dice[dieId].locked);
    },
    lancerLesDes() {
      // enléve 1 aux alncers disponibles
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
        // si le dés est dans le tableau des dés à conserver, ne pas lancer
        console.log(this.dieToLock);

        /*  console.log(this.dieToLock[die]); */

        /*  const diceId = this.dice.id;
          console.log("ici");
          if (this.dieToLock[die] === diceId) {
            return;
          } else {
         
          } */
      }
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
  height: 200px;
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
    background-color: #f0f;
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
</style>


