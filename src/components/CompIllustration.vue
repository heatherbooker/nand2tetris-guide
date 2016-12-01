<template>

  <div class="">
  <div>Resulting computation: {{operand1}} {{operator}} {{operand2}}</div>
  <div>Resulting jump operation: {{jump}}</div>
  </div>

</template>


<script>

  export default {
    props: ['operator', 'operand1', 'operand2', 'jump'],
    data () {
      return {

      };
    }
  };

</script>


<style>
  


</style>
