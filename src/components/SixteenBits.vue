<template>
  
  <div class="nand-16bitInstructions center mv4">
    <bit-group
      v-for="(bitGroup, i) in bitGroups"
      :bitGroup="bitGroup"
      :tooltipInfo="tooltipInfo"
    ></bit-group>
  </div>

</template>


<script>
  
  import BitGroup from './BitGroup';
  import info from '../assets/sixteenBitsInfo.json';

  export default {
    components: {
      BitGroup
    },
    props: ['initialBitgroups'],
    data () {
      return {
        bits: [],
        colors: ['blue', 'green', 'yellow', 'pink', 'orange', 'purple'],
        tooltipInfo: info
      };
    },
    methods: {
      assignColors (bits, colors) {
        for (let i = 0; i < bits.length; i++) {
          let colorI = i;
          while (colorI >= colors.length) {
            colorI -= colors.length;
          }
          bits[i].color = colors[colorI];
        }
      },
      enumerateBits (bitsInGroup) {
        let bits = [];
        for (let i = 0; i < bitsInGroup.num; i++) {
          let name;
          if (bitsInGroup.num <= 1) {
            name = bitsInGroup.type;
          } else {
            name = bitsInGroup.type + (i + 1);
          }
          bits.push({
            name
          });
          console.log(bits);
          this.assignColors(bits, this.colors);
        }
        return bits;
      }
    },
    created () {
      this.bits = this.initialBitgroups.reduce((allBits, bitGroup) => {
        return this.enumerateBits(bitGroup);
      });
    }
  };

</script>

<style>
  
  .nand-16bitInstructions {
    display: flex;
  }
  code {
    background-color: #E1E1E1;
    padding: 1px 4px;
  }
  
</style>
