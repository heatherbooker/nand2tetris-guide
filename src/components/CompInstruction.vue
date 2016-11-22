<template>
  
  <div>
    <h4 class="f3 lh-copy">Computation Instruction</h4>
    <p></p>
    <sixteen-bits :initial-bitgroups="bitGroups"></sixteen-bits>
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
    }
  };

</script>
