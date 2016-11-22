<template>

  <div class="nand-sidebar">
    <ul class="nand-sidebar--list">
      <li><a href="">Intro</a></li>
      <li><a href="">Chapter 1</a></li>
      <li><a href="">Chapter 2</a></li>
      <li><a href="">Chapter 3</a></li>
      <li><a href="">Chapter 4</a></li>
      <li><a href="">Chapter 5</a></li>
    </ul>
  </div>

</template>


<script>

export default {
  name: 'sidebar',
  data () {
    return {
    };
  }
};

</script>


<style scoped>

.nand-sidebar {
  width: 15%;
}

h1, h2 {
  font-weight: normal;
}

.nand-sidebar--list {
  list-style-type: none;
}

.nand-sidebar--list li a {
  text-decoration: none;
}

</style>
