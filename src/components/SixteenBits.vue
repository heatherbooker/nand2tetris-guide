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
        bitGroups: [],
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
      }
    },
    created () {
      this.bitGroups = this.initialBitgroups;
      this.assignColors(this.bitGroups, this.colors);
    }
  };

</script>

<style>
  
  .nand-16bitInstructions {
    display: flex;
  }

</style>
