<template>
  
  <div>
    <h4 class="f3 lh-copy">Computation Instruction</h4>
    <p>The <b>computation instruction</b> is similarly a group of 16 bits, the most significant (left-most) of which is <code>1</code>. The next 2 digits to the right are not used.</p>
    <p>The remaining 13 bits can be further split into subgroups. Each subgroup controls an aspect of the instruction - <b>what</b>, <b>where</b>, and what's <b>next</b>.</p>
    <sixteen-bits
      :initial-bits="bits"
      @toggleBits="toggleBits"
      :info="info.bits"
    ></sixteen-bits>
    <comp-illustration
      :operand1="operand1"
      :operand2="operand2"
      :operator="operator"
      :jump="jump || 'No jump'"
    ></comp-illustration>
  </div>

</template>


<script>

  import SixteenBits from './SixteenBits';
  import CompIllustration from './CompIllustration';

  export default {
    components: {
      SixteenBits,
      CompIllustration
    },
    props: ['info'],
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
          num: 2,
          startIndex: 1,
          color: ''
        }, {
          type: 'a',
          num: 1,
          startIndex: 3,
          color: ''
        }, {
          type: 'c',
          num: 6,
          startIndex: 4,
          color: ''
        }, {
          type: 'd',
          num: 3,
          startIndex: 10,
          color: ''
        }, {
          type: 'j',
          num: 3,
          startIndex: 13,
          color: ''
        }],
        operand1: 'D',
        operand2: 'A',
        operator: '&',
        jump: null
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
        this.bits[index].value = Number(!this.bits[index].value);
        const computation = this.info.comp_instructions[this.instruction.slice(4,10)];
        if (!computation) {
          this.operand1 = ' -- Not a valid instruction --';
          this.operator = '';
          this.operand2 = '';
        } else {
          this.operand1 = computation[0];
          this.operator = computation[1];
          this.operand2 = computation[2];
        }
        console.log(this.instruction.slice(12));
        this.jump = this.info.jump_instructions[this.instruction.slice(13)];
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
    computed: {
      instruction () {
        return this.bits.map(bit => bit.value).join('');
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

<style type="text/css">
  code {
    background-color: #E1E1E1;
    padding: 1px 4px;
  }
</style>
