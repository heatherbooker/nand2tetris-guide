<template>
  
  <div class="nand-bit">
    {{15 - index}}
    <div class="nand-bit-box" :class="colorClass">
      <label :class="labelClass">
        {{initialName}}
      </label>
      <input
        class="nand-bit-box-input"
        type="text"
        v-model="name"
        @focus="shrinkLabel"
        @blur="growLabelIfEmpty"
        spellcheck="false"
      >
    </div>
  </div>
  
</template>


<script>
  
  export default {
    
    props: ['index', 'initialName', 'initialValue', 'color', 'tooltipInfo'],

    data () {
      return {
        colorClass: 'nand-bit-box__color_' + this.color,
        labelClass: 'nand-bit-label--shrink',
        name: this.initialValue || ''
      };
    },
    mounted () {
      console.log(this.initialValue);

      let content = '';
      let title = '';

      if (this.tooltipInfo[this.initialName]) {
        content = this.tooltipInfo[this.initialName].content;
        title = this.tooltipInfo[this.initialName].title;
      }

      new Opentip(this.$el, content, title);
    },
    methods: {
      shrinkLabel () {
        this.labelClass = 'nand-bit-label--shrink';
      },
      growLabelIfEmpty () {
        if (!this.name) {
          this.labelClass = 'nand-bit-label';
        }
      }
    }
  };

</script>


<style lang="scss">
  
  .nand-bit {
    text-align: center;
    width: 50px;
    flex: 1;
  }

  .nand-bit-box {
    border: 1px solid grey;
    height: 50px;
    color: #fff;
    font-weight: bold;
  }

  .nand-bit-label {
    position: relative;
    top: 30%;
  }

  .nand-bit-label--shrink {
    font-size: 10pt;
    opacity: .75;
    position: relative;
    left: -10px;
  }

  .nand-bit-box-input {
    background-color: inherit;
    border: none;
    width: 100%;
    color: inherit;
    text-align: center;
    &:focus {
      outline: none;
    }
  }

  .nand-bit-box__color_blue {
    background-color: #2e284a;
  }

  .nand-bit-box__color_green {
    background-color: #494566;
  }

  .nand-bit-box__color_yellow {
    background-color: #5b5a86;
  }

  .nand-bit-box__color_pink {
    background-color: #a5884c;
  }

  .nand-bit-box__color_orange {
    background-color: #d2c791;
  }

  .nand-bit-box__color_purple {
    background-color: #a86b45;
  }

</style>
