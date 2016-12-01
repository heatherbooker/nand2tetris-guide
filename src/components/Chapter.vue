<template>

  <div :class="['nand-chapter w-80 center mv4', classWithId]">
  
    <h2 class="nand-chapter-title f2 mb5">Chapter 4</h2>
    <section>
      <p>Chapter 4 introduces two types of 16-bit instructions: <b>address</b> instructions and <b>computation</b> instructions.</p>
      <p><span>The most significant (left-most) bit</span> determines whether an instruction is an address (0) or a computation (1).</p>
      <addr-instruction></addr-instruction>
      <comp-instruction @toggleBits="updateComputation"></comp-instruction>
      <comp-illustration
        :operand1="operand1"
        :operand2="operand2"
        :operator="operator"
      ></comp-illustration>
      <h4 class="f3">Assembly</h4>
      <p>The <span id="nand-tt-assembly">assembly</span> language </p>
    </section>
  </div>

</template>


<script>

  import AddrInstruction from './AddrInstruction';
  import CompInstruction from './CompInstruction';
  import CompIllustration from './CompIllustration';
  
  export default {
    props: ['id'],
    data () {
      return {
        classWithId: 'nand-chapter' + this.id,
        operand1: 'D',
        operand2: 'A',
        operator: '&'
      };
    },
    components: {
      'addr-instruction': AddrInstruction,
      'comp-instruction': CompInstruction,
      'comp-illustration': CompIllustration
    },
    methods: {
      updateComputation (e) {
      }
    },
    mounted () {
      const tooltipElements = [];
      tooltipElements.push({
        el: document.getElementById('nand-tt-assembly'),
        content: '<em>Assembly</em> language is a type of low-level language, a step above binary, and more readable for humans.'
      });
      tooltipElements.forEach(el => {
        new Opentip(el.el, el.content, el.title && el.title);
      })
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

.nand-chapter p {
  line-height: 1.5;
  margin-bottom: 30px;
}

</style>
