<template>

  <div id="app">
    <intro></intro>
    <chapter id="5"></chapter>
  </div>

</template>


<script>

import Sidebar from './components/Sidebar';
import Intro from './components/Intro';
import Chapter from './components/Chapter';

export default {
  name: 'app',
  components: {
    Sidebar,
    Intro,
    Chapter
  }
};

</script>


<style>

#app {
  font-family: 'Open Sans', sans-serif;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  margin: 0;
}

button {
  border: none;
  background-color: inherit;
  outline: none;
}

</style>
