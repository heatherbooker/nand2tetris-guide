<template>
  
  <div>
    <h4 class="f3 lh-copy">Computation Instruction</h4>
    <p>The <b>computation instruction</b> is similarly a group of 16 bits, the most significant (left-most) of which is <code>1</code>. The next 2 digits to the right are not used.</p>
    <p>The remaining 13 bits can be further split into subgroups. Each subgroup controls an aspect of the instruction - 
    <b @mouseover="toggleHoverEffect" @mouseleave="toggleHoverEffect">what</b>,
    <b @mouseover="toggleHoverEffect" @mouseleave="toggleHoverEffect">where</b>, and what's
    <b @mouseover="toggleHoverEffect" @mouseleave="toggleHoverEffect">next</b>.
    </p>
    <sixteen-bits
      :initial-bits="bits"
      :hovered="hovered"
      @toggleBits="handleToggleBit"
      :info="info.bits"
    ></sixteen-bits>
    <comp-illustration
      :operand1="operand1 || ' -- Not a valid instruction --'"
      :operand2="operand2"
      :operator="operator"
      :jump="jump"
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
        hovered: false,
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

      handleToggleBit (index) {

        this.bits[index].value = Number(!this.bits[index].value);

        const computation = this.info.comp_instructions[this.instruction.slice(4,10)];
        this.operand1 = computation && computation[0] || '';
        this.operator = computation && computation[1] || '';
        this.operand2 = computation && computation[2] || '';

        if (Number(this.instruction.slice(3, 4))) {
          this.operand1 = this.operand1.replace('A', 'M');
          this.operand2 = this.operand2.replace('A', 'M');
        }

        this.jump = this.info.jump_instructions[this.instruction.slice(13)];
      },

      toggleHoverEffect (event) {
        if (event.type == 'mouseleave') {
          this.hovered = null;
        } else {
          this.hovered = event.target.textContent;
        }
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


<style>

  code {
    background-color: #E1E1E1;
    padding: 1px 4px;
  }

</style>
