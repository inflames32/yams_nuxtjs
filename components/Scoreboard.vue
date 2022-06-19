<template>
  <div class="scoreboard">
    <div class="score_array">
      <div class="left">
        <div>
          <div
            :class="`${line.name}` + ' line'"
            v-for="(line, idx) in left"
            :key="idx"
          >
            <div>
              {{ line.name }} :
              <span>{{ line.score }}</span>
            </div>
            <div :class="`${line.score}`">{{ line.score }}</div>
          </div>
        </div>
      </div>
      <div class="right">
        <div>
          <div class="as line" v-for="(line, idx) in right" :key="idx">
            <span>{{ line.name }} :</span>
            <div class="score_as">{{ line.score }}</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Scoreboard",
  data() {
    return {
      left: [
        { name: "Un", score: null },
        { name: "Deux", score: null },
        { name: "Trois", score: null },
        { name: "Quatre", score: null },
        { name: "Cinq", score: null },
        { name: "Six", score: null },
        { name: "Total", score: null },
        { name: "Bonus>62", score: null },
        { name: "Total+Bonus", score: null },
      ],
      right: [
        { name: "Plus", score: null },
        { name: "Moins", score: null },
        { name: "Total Plus - Moins", score: null },
        { name: "Suite", score: null },
        { name: "Full", score: null },
        { name: "Carré", score: null },
        { name: "Yams", score: null },
        { name: "Total3", score: null },
        { name: "Total de la partie", score: null },
      ],

      totalAs: "112341351",
      methods: {
        scoreAs() {},
      },
      props: {
        /* scores: Array, */
        sumAs: Function,
      },
    };
  },
};
</script>

<style lang="scss">
.scoreboard {
  width: 100%;
  height: 640px;
}
.score_array {
  width: 88%;
  display: flex;
  justify-content: center;
  margin: auto;
}
.left,
.right {
  width: 45%;
  margin: 15px;
}
.line {
  display: flex;
  justify-content: left;
  align-items: center;
  border: rgb(77, 77, 237) solid 2px;
  border-radius: 5px;
  height: 40px;
  margin: 10px;
  padding: 5px;
}
</style>
<!-- <div class="scoreboard">
      <div class="score_array">
        <div class="left">
          <div class="line">
            <div @click="sumAs">AS : {{ this.scores.scoreAs }}</div>
          </div>
          <div class="line">
            <div>DEUX : {{ this.scores.scoreTwo }}</div>
          </div>
          <div class="line">
            <div>TROIS : '2'</div>
          </div>
          <div class="line">
            <div>QUATRE : '2'</div>
          </div>
          <div class="line">
            <div>CINQ: '2'</div>
          </div>
          <div class="line">
            <div>SIX : '2'</div>
          </div>
          <div class="line">
            <div>TOTAL : '2'</div>
          </div>
          <div class="line">
            <div>Bonus > 62 : '2'</div>
          </div>
          <div class="line">
            <div>TOTAL + BONUS : '2'</div>
          </div>
        </div>
        <div class="right">
          <div class="line">
            <div>PLUS : '2'</div>
          </div>
          <div class="line">
            <div>MOINS : '2'</div>
          </div>
          <div class="line">
            <div>TOTAL PLUS MOINS : '2'</div>
          </div>
          <div class="line">
            <div>SUITE : '2'</div>
          </div>
          <div class="line">
            <div>FULL : '2'</div>
          </div>
          <div class="line">
            <div>CARRE : '2'</div>
          </div>
          <div class="line">
            <div>YAMS : '2'</div>
          </div>
          <div class="line">
            <div>TOTAL : '2'</div>
          </div>
          <div class="line">
            <div>RESULTAT FINAL : '2'</div>
          </div>
        </div>
      </div>
    </div> -->