<template>
  
  <div class="nand-bit">
    {{15 - index}}
    <div class="nand-bit--box" :class="colorClass">
      <button class="nand-bit--box-button" @click="toggleValue">
        {{bit.value}}
      </button>
    </div>
    {{bit.name}}
  </div>
  
</template>


<script>
  
  export default {
    
    props: ['index', 'bit', 'tooltipInfo', 'hovered'],

    data () {
      return {
        // colorClass: 'nand-bit--box__color_' + this.bit.color
      };
    },

    computed: {
      colorClass () {
        console.log(this.hovered);
        return 'nand-bit--box__color_' + this.bit.color + (this.hovered ? '_dark' : '');
      }
    },

    methods: {
      toggleValue() {
        this.$emit('toggleBit', this.index);
      }
    },
    mounted () {

      let content = '';
      let title = '';

      if (this.tooltipInfo[this.bit.name]) {
        content = this.tooltipInfo[this.bit.name].content;
        title = this.tooltipInfo[this.bit.name].title;
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

  .nand-bit--box__color_blue_dark {
    background-color: #272240;
  }

  .nand-bit--box__color_green_dark {
    background-color: #413E5C;
  }

  .nand-bit--box__color_yellow_dark {
    background-color: #55547D;
  }

  .nand-bit--box__color_pink_dark {
    background-color: #9C8047;
  }

  .nand-bit--box__color_orange_dark {
    background-color: #C7BD89;
  }

  .nand-bit--box__color_purple_dark {
    background-color: #9E6541;
  }
</style>
