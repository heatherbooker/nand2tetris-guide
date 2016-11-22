<template>
  
  <div>
    <h4 class="f3 lh-copy">Address Instruction</h4>
    <p>The <b>address instruction</b> is a group of 16 bits, the first of which will always be a <code>1</code>. </p>
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
          num: 15,
          startIndex: 1,
          color: ''
        }]
      };
    },
  };

</script>
