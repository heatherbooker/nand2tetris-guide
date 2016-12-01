<template>
  
  <div class="nand-16bitInstructions center mv4">
    <bit
      v-for="(bit, i) in bits"
      :index="i"
      :bit="bit"
      :tooltipInfo="tooltipInfo"
      @toggleBit="toggleBits"
    ></bit>
  </div>

</template>


<script>
  
  import Bit from './Bit';

  export default {
    components: {
      Bit
    },
    props: ['initialBits', 'info'],
    data () {
      return {
        bits: this.initialBits,
        colors: ['blue', 'green', 'yellow', 'pink', 'orange', 'purple'],
        tooltipInfo: this.info
      };
    },
    methods: {
      toggleBits (index) {
        this.$emit('toggleBits', index);
      }
    }
  };

</script>

<style>
  
  .nand-16bitInstructions {
    display: flex;
  }

</style>
