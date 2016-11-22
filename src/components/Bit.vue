<template>
  
  <div class="nand-bit">
    {{index}}
    <div class="nand-bit--box" :class="colorClass">
      {{name}}
    </div>
  </div>
  
</template>


<script>
  
  export default {
    
    props: ['index', 'name', 'type', 'color', 'tooltipInfo'],

    data () {
      return {
        colorClass: 'nand-bit--box__color_' + this.color
      };
    },

    mounted () {

      let content = '';
      let title = '';

      if (this.tooltipInfo[this.name]) {
        content = this.tooltipInfo[this.name].content;
        title = this.tooltipInfo[this.name].title;
      }

      new Opentip(this.$el, content, title);
    }
  };

</script>


<style>
  
  .nand-bit {
    text-align: center;
    width: 50px;
    flex: 1;
  }

  .nand-bit--box {
    border: 1px solid grey;
    height: 50px;
    display: flex;
    justify-content: center;
    align-items: center;
    color: #fff;
    font-weight: bold;
  }

  .nand-bit--box__color_blue {
    background-color: #2e284a;
  }

  .nand-bit--box__color_green {
    background-color: #494566;
  }

  .nand-bit--box__color_yellow {
    background-color: #5b5a86;
  }

  .nand-bit--box__color_pink {
    background-color: #a5884c;
  }

  .nand-bit--box__color_orange {
    background-color: #d2c791;
  }

  .nand-bit--box__color_purple {
    background-color: #a86b45;
  }

</style>
