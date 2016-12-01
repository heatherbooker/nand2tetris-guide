<template>
  
  <div class="mv4">
    <h4 class="f3 lh-copy mv4">Address Instruction</h4>
    <p>The <b>address instruction</b> is a group of 16 bits, the most significant (left-most) of which is <code>0</code>. </p>
    <p>The remaining 15 bits of the address instruction will be composed of 0s and 1s, which taken together denote a location in memory, ie. an address.</p>
    <sixteen-bits :initial-bits="bits" @toggleBits="toggleBits"></sixteen-bits>
  </div>

</template>


<script>
  
  import SixteenBits from './SixteenBits';

  export default {
    components: {
      SixteenBits
    },
    data () {
      return {
        bits: [],
        colors: ['blue', 'green', 'yellow', 'pink', 'orange', 'purple'],
        bitGroups: [{
          type: 'v',
          num: 1,
          startIndex: 0,
          color: ''
        }, {
          type: 'x',
          num: 15,
          startIndex: 1,
          color: ''
        }]
      };
    },
    methods: {
      enumerateBits (bitGroup) {
        let bits = [];
        for (let i = 0; i < bitGroup.num; i++) {
          let name;
          if (bitGroup.num <= 1) {
            name = bitGroup.type;
          } else {
            name = bitGroup.type + (i + 1);
          }
          bits.push({
            name,
            type: bitGroup.type,
            color: bitGroup.color,
            value: 0
          });
        }
        return bits;
      },
      toggleBits (index) {
        this.$emit('toggleBits');
        this.bits[index].value = Number(!this.bits[index].value);
      },
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
      this.assignColors(this.bitGroups, this.colors);
      this.bits = this.bitGroups.reduce((bits, bitGroup) => {
        return bits.concat(this.enumerateBits(bitGroup));
      }, []);
    }
  };

</script>
