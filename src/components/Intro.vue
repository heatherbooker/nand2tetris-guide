<template>
  <div>  
    <div class="nand-intro-container">
      <div class="nand-intro w-80 center">
        <h2 class="f2"><span>Welcome</span> to a <span>friendlier</span> way to do <span>Nand to Tetris.</span></h2>
        <p class="w-50">Explore the intricate details of how computers work, from low-level hardware intricacies <em>(Nand)</em> to the highest levels of abstraction <em>(Tetris)</em>.</p>
        <span v-on:click="scroll(false)" class="nand-down-arrow"></span>
      </div>
    </div>
    <div class="nand-intro-preface-container">
      <div class="nand-intro-preface w-70 center lh-copy">
        <h3 class="f3">Story</h3>
        <p>Nand to Tetris is a well known course (accompanied by the book <em> The Elements of Computing Systems</em>), which takes participants from learning about logic gates and hardware, through building a "computer" and virtual machine, all the way to implementing an operating system and a program on top of it. It is a great resource and has helped and taught many people. </p>
        <p>I jumped into Nand to Tetris with no math, engineering or electrical background - just experience in front end web development. It was totally overwhelming for me and I had no idea what I was even supposed to be trying to learn; if it hadn't been for some wonderful friends, I would never have made it through the first few pages.</p>
        <p>Thus sprung the idea for this guide - other people were echoing that they wish they had a group or guide to smooth their progress through the course, and I felt that visual demonstrations of the concepts would be an excellent addition to the resources currently available.</p>
        <p>With that, I hope you enjoy your trip from low-level "basics" to high-level abstractions. Buckle up and go learn some things!</p>
      </div>
      <span v-on:click="scroll(true)" class="nand-down-arrow-2"></span>
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
    scroll (isSecondScroll) {
      var scrollEl = document.body;
      var duration = 500;
      var start = scrollEl.scrollTop;
      var nandIntroHeight = document.querySelector('.nand-intro-container').scrollHeight;
      var end = isSecondScroll ? nandIntroHeight * 2 : nandIntroHeight;
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
  padding-top: 20%;
  color: #fff;
}

.nand-intro-preface-container {
  background-color: #494566;
  width: 100%;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  color: #D9D9D9;
}

.nand-intro-preface p {
  font-size: 15pt;
}

.nand-intro-container {
  background-color: #2e284a;
  min-height: 100vh;
  width: 100%;
}

.nand-down-arrow, .nand-down-arrow-2 {
  background: url(../assets/down-arrow.svg) no-repeat center;
  width: 50px;
  height: 40px;
  position: relative;
  top: 16vh;
  &:hover {
    cursor: pointer;
  }
}

.nand-down-arrow-2 {
  position: absolute;
  top: 188vh;
}

</style>
