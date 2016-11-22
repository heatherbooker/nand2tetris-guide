<template>
  <div class="nand-intro-container">
    <div class="nand-intro w-80 center">
      <h2 class="f2"><span>Welcome</span> to a <span>friendlier</span> way to do <span>Nand to Tetris.</span></h2>
      <p class="w-50">Explore the intricate details of how computers work, from low-level hardware intricacies <em>(Nand)</em> to the highest levels of abstraction <em>(Tetris)</em>.</p>
      <span v-on:click="scroll" class="nand-down-arrow"></span>
    </div>
  </div>
</template>


<script>
  
export default {
  data () {
    return {

    };
  },
  methods: {
    scroll () {
      var scrollEl = document.body;
      var duration = 500;
      var start = scrollEl.scrollTop;
      var end = this.$el.scrollHeight;
      var change = end - start;
      var increment = 20;

      function easeInOut(currentTime, start, change, duration) {
        currentTime /= duration / 2;
        if (currentTime < 1) {
          return change / 2 * currentTime * currentTime + start;
        }
        currentTime -= 1;
        return -change / 2 * (currentTime * (currentTime - 2) - 1) + start;
      }

      function animate(elapsedTime) {

        elapsedTime += increment;
        var position = easeInOut(elapsedTime, start, change, duration);
        scrollEl.scrollTop = position;

        if (elapsedTime < duration) {
          setTimeout(function() {
            animate(elapsedTime);
          }, increment)
        }
      }
      animate(0);
    }
  }
};

</script>

<style lang="scss">

.nand-intro p {
  margin: 30px 0px;
  font-size: 16pt;
  line-height: 1.4;
}

.nand-intro {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 20%;
  margin-bottom: 60px;
  color: #fff;
}

.nand-intro-container {
  background-color: #2e284a;
  min-height: 100vh;
  margin: 0;
  width: 100%;
}

.nand-down-arrow {
  background: url(../assets/down-arrow.svg) no-repeat center;
  width: 50px;
  height: 40px;
  position: relative;
  top: 16vh;
  &:hover {
    cursor: pointer;
  }
}

</style>
