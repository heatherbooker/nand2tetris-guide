<template>
  
  <div class="nand-ch5-bitGroup">
    <bit
      v-for="(bit, i) in bits"
      :index="bitGroup.startIndex + i"
      :initialName="bit.name"
      :initialValue="bitGroup.val"
      :color="bitGroup.color"
      :tooltipInfo="tooltipInfo"
    ></bit>
  </div>

</template>


<script>
  
  import Bit from './Bit';

  export default {
    components: {
      Bit
    },
    props: ['bitGroup', 'tooltipInfo'],
    data () {
      return {
        bits: []
      };
    },
    methods: {
      enumerateBits () {
        let bits = [];
        for (let i = 0; i < this.bitGroup.num; i++) {
          let name;
          if (this.bitGroup.num <= 1) {
            name = this.bitGroup.type;
          } else {
            name = this.bitGroup.type + (i + 1);
          }
          bits.push({
            name
          });
        }
        this.bits = bits;
      }
    },
    mounted () {
      this.enumerateBits(this.bits);
    }
  };

</script>

<style>
  
  .nand-ch5-bitGroup {
    display: flex;
    flex-direction: row;
  }


</style>
