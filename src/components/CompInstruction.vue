<template>
  
  <div>
    <h4 class="f3 lh-copy">Computation Instruction</h4>
    <p></p>
    <p>The <b>computation instruction</b> is similarly a group of 16 bits, the most significant (left-most) of which is <code>1</code>. The next 2 digits to the right are not used.</p>
    <p>The remaining 13 bits can be further split into subgroups. Each subgroup controls an aspect of the instruction - <b>what</b>, <b>where</b>, and what's <b>next</b>.</p>
    <sixteen-bits :initial-bitgroups="bitGroups"></sixteen-bits>

    <div>

      <div class="nand-ch5-destinations">
        <div class="nand-ch5-cpu">
          <div>
            A
          </div>
          <div>
            D
          </div>
        </div>
        <div>
          <div>
            M[A]
          </div>
        </div>
      </div>

      <div>
        <input type="text" v-model="operand1">
        <input type="text" v-model="operator">
        <input type="text" v-model="operand2">
      </div>
      <div>
        <input type="text" v-model="operand1Example">
        <input type="text" v-model="operator">
        <input type="text" v-model="operand2Example">
      </div>

    </div>

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
        operand1: 'A',
        operand2: 'D',
        operand1Example: 4,
        operand2Example: 3,
        operator: '+',
        bitGroups: [{
          type: 'v',
          num: 1,
          val: 1,
          startIndex: 0,
          color: ''
        }, {
          type: 'x',
          num: 2,
          val: 1,
          startIndex: 1,
          color: ''
        }, {
          type: 'a',
          num: 1,
          val: '0',
          startIndex: 3,
          color: ''
        }, {
          type: 'c',
          num: 6,
          val: '0',
          startIndex: 4,
          color: ''
        }, {
          type: 'd',
          num: 3,
          val: '0',
          startIndex: 10,
          color: ''
        }, {
          type: 'j',
          num: 3,
          val: '0',
          startIndex: 13,
          color: ''
        }]
      };
    }
  };

</script>

<style lang="scss" scoped>

  .nand-ch5-cpu {
    border: 1px solid grey;
  }
  .nand-ch5-destinations {
    border: 1px solid grey;
    width: 10%;
    padding: 8px;
  }
  
</style>
