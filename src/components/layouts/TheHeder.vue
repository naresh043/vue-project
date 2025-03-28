<template>
    <header class="header">
      <h1>{{ title }}</h1>
    </header>
  </template>
  
  <script>
  export default {
    props: ["title"],
  };
  </script>
  
  <style scoped>
  .header {
    background-color: #42b983;
    color: white;
    padding: 1rem;
    text-align: center;
    font-size: 1.5rem;
    font-weight: bold;
  }
  </style>
  