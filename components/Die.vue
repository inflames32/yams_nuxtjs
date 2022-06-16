<template>
  <div class="die_container">
    <div class="die">
      <img class="die_img" src="~/assets/img/dice/1.svg" alt="" />
    </div>
    <!-- <div class="die">
      <img class="die_img" src="~/assets/img/dices/2.svg" alt="" />
    </div>
    <div class="die">
      <img class="die_img" src="~/assets/img/dices/3.svg" alt="" />
    </div>
    <div class="die">
      <img class="die_img" src="~/assets/img/dices/4.svg" alt="" />
    </div>
    <div class="die">
      <img class="die_img" src="~/assets/img/dices/5.svg" alt="" />
    </div>
    <div class="die">
      <img class="die_img" src="~/assets/img/dices/6.svg" alt="" />
    </div> -->
  </div>
</template>


<script>
export default {
  name: "Die",
  data() {
    return {};
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
