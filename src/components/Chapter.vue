<template>

  <div :class="['nand-chapter w-80 center', classWithId]">
  
    <h2 class="nand-chapter-title f2">Chapter {{id}}</h2>
    <p>Chapter 5 introduces two types of 16-bit instructions: <b>address</b> instructions and <b>computation</b> instructions.</p>
    <addr-instruction></addr-instruction>
    <comp-instruction></comp-instruction>
  </div>

</template>


<script>

  import AddrInstruction from './AddrInstruction';
  import CompInstruction from './CompInstruction';
  
  export default {
    props: ['id'],
    data () {
      return {
        classWithId: 'nand-chapter' + this.id
      };
    },
    components: {
      'addr-instruction': AddrInstruction,
      'comp-instruction': CompInstruction
    }
  };

</script>


<style>
  
.nand-chapter {
  padding-top: 40px;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.nand-chapter-title {
  width: 100%;
}

</style>
