<template>

  <div class="">
  <div>Resulting computation: {{operand1}} {{operator}} {{operand2}}</div>
  </div>

</template>


<script>

  export default {
    props: ['operator', 'operand1', 'operand2'],
    data () {
      return {

      };
    }
  };

</script>


<style>
  


</style>
