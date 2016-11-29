<template>
  
  <div class="nand-bit">
    {{15 - index}}
    <div class="nand-bit--box" :class="colorClass">
      <button class="nand-bit--box-button" @click="toggleValue">
        {{value}}
      </button>
    </div>
    {{initialName}}
  </div>
  
</template>


<script>
  
  export default {
    
    props: ['index', 'initialName', 'type', 'color', 'tooltipInfo'],

    data () {
      return {
        colorClass: 'nand-bit--box__color_' + this.color,
        value: 0
      };
    },
    methods: {
      toggleValue() {
        this.value = Number(!this.value);
        this.$emit('toggleBit', 'an argument');
      }
    },
    mounted () {

      let content = '';
      let title = '';

      if (this.tooltipInfo[this.initialName]) {
        content = this.tooltipInfo[this.initialName].content;
        title = this.tooltipInfo[this.initialName].title;
      }

      new Opentip(this.$el, content, title);
    }
  };

</script>


<style lang="scss">
  
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

  .nand-bit--box-button {
    background-color: inherit;
    border: none;
    width: 50px;
    height: 100%;
    color: inherit;
    text-align: center;
    &:focus {
      outline: none;
    }
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
