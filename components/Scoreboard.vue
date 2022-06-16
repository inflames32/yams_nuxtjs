<template>
  <div class="scoreboard">
    <div class="score_array">
      <div class="left">
        <div>
          <div class="as line" v-for="(line, idx) in left" :key="idx">
            <span>{{ line.name }}: </span>
            <div class="score_as">{{ line.score }}</div>
          </div>
        </div>
      </div>
      <div class="right">
        <div>
          <div class="as line" v-for="(line, idx) in right" :key="idx">
            <span>{{ line.name }}</span>
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
        { name: "As", score: "" },
        { name: "Two", score: "" },
        { name: "Three", score: "" },
        { name: "Four", score: "" },
        { name: "Five", score: "" },
        { name: "Six", score: "" },
        { name: "Total", score: "" },
        { name: "Bonus>62", score: "" },
        { name: "Total+Bonus", score: "" },
      ],
      right: [
        { name: "Plus", score: "" },
        { name: "Less", score: "" },
        { name: "Straight", score: "" },
        { name: "Full", score: "" },
        { name: "Yams", score: "" },
        { name: "Total3", score: "" },
        { name: "FinalResult", score: "" },
      ],

      totalAs: "112341351",
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
  display: flex;
  border: rgb(77, 77, 237) solid 2px;
  border-radius: 5px;
  height: 40px;
  margin: 10px;
  padding: 5px;
}
</style>
