<template>
  <div class="scoreboard">   
    <div class="score_array">
      <div class="left">
        <div class="as line">
          <span>AS</span>
          <div class="score_as">{{this.totalAs}}</div>
        </div>
        <div class="two line">
          <span>DEUX</span>
          <div class="score_two">{{this.score[1].totalTwo}}</div>
        </div>
        <div class="as line">
          <span>TROIS</span>
          <div class="score_as">3</div>
        </div>
        <div class="as line">
          <span>QUATRE</span>
          <div class="score_as">4</div>
        </div>
        <div class="as line">
          <span>CING</span>
          <div class="score_as">8</div>
        </div>
        <div class="as line">
          <span>SIX</span>
          <div class="score_as">6</div>
        </div>
        <div class="as line">
          <span>TOTAL</span>
          <div class="score_as">6</div>
        </div>
        <div class="as line">
          <span>BONUS > 62</span>
          <div class="score_as">6</div>
        </div>
        <div class="as line">
          <span>TOTAL + BONUS</span>
          <div class="score_as"></div>
        </div>
      </div>
      <div class="right">
        <div class="as line">
          <span>Plus</span>
          <div class="score_as">1</div>
        </div>
        <div class="two line">
          <span>Moins</span>
          <div class="score_two">2</div>
        </div>
        <div class="as line">
          <span>TOTAL 2</span>
          <div class="score_as">3</div>
        </div>
        <div class="as line">
          <span>Suite</span>
          <div class="score_as">4</div>
        </div>
        <div class="as line">
          <span>Full</span>
          <div class="score_as">8</div>
        </div>
        <div class="as line ">
          <span>Carré</span>
          <div class="score_as">6</div>
        </div>
        <div class="as line ">
          <span>Yams</span>
          <div class="score_as">6</div>
        </div>
        <div class="as line ">
          <span>TOTAL 3</span>
          <div class="score_as">6</div>
        </div>
        <div class="as line ">
          <span>Résultat final</span>
          <div class="score_as"></div>
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
      score: [
        { name: "As", totalAs: "4" },
        { name: "As", totalTwo: "8" },
      ],
      totalAs: "112341351",
    };
  },
};
</script>

<style lang="scss">
.scoreboard {
  width: 100%;
  height: 550px;
}
.score_array {
  width: 80%;
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
  border: rgb(77, 77, 237) solid 1px;
  border-radius: 5px;
  height: 40px;
  margin: 10px;
}
</style>
