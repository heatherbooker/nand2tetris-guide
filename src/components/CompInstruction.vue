<template>
  
  <div>
    <h4 class="f3 lh-copy">Computation Instruction</h4>
    <p></p>
    <p>The <b>computation instruction</b> is similarly a group of 16 bits, the most significant (left-most) of which is <code>1</code>. The next 2 digits to the right are not used.</p>
    <p>The remaining 13 bits can be further split into subgroups. Each subgroup controls an aspect of the instruction - <b>what</b>, <b>where</b>, and what's <b>next</b>.</p>
    <sixteen-bits :initial-bitgroups="bitGroups" @toggleBits="toggleBits"></sixteen-bits>
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
        }]
      };
    },
    methods: {
      toggleBits () {
        this.$emit('toggleBits');
        console.log('emiting');
      }
    }
  };

</script>

<style type="text/css">
  code {
    background-color: #E1E1E1;
    padding: 1px 4px;
  }
</style>
