<template>
  
  <div class="mv4">
    <h4 class="f3 lh-copy mv4">Address Instruction</h4>
    <p>The <b>address instruction</b> is a group of 16 bits, the most significant (left-most) of which is <code>0</code>. </p>
    <p>The remaining 15 bits of the address instruction will be composed of 0s and 1s, which taken together denote a location in memory, ie. an address.</p>
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
