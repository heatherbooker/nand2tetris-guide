<template>

  <div :class="['nand-chapter w-80 center mv4', classWithId]">
  
    <h2 class="nand-chapter-title f2 mb5">Chapter 4</h2>
    <section>
      <p>Chapter 4 introduces two types of 16-bit instructions: <b>address</b> instructions and <b>computation</b> instructions.</p>
      <p><span>The most significant (left-most) bit</span> determines whether an instruction is an address (0) or a computation (1).</p>
      <addr-instruction :info="info"></addr-instruction>
      <comp-instruction
        @toggleBits="updateComputation"
        :info="info"
      ></comp-instruction>
      <h4 class="f3">Assembly</h4>
      <p>The <span id="nand-tt-assembly">assembly</span> language </p>
    </section>
  </div>

</template>


<script>

  import info from '../assets/sixteenBitsInfo.json';
  import AddrInstruction from './AddrInstruction';
  import CompInstruction from './CompInstruction';
  
  export default {
    props: ['id'],
    data () {
      return {
        info,
        classWithId: 'nand-chapter' + this.id
      };
    },
    components: {
      AddrInstruction,
      CompInstruction
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
      });
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
