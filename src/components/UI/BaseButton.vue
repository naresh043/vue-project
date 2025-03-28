<template>
    <button :type="type" :class="mode">
      <slot></slot>
    </button>
  </template>
  
  <script>
  export default {
    props: ["type", "mode"]
  };
  </script>
  
  <style scoped>
  button {
    font-size: 1rem;
    padding: 10px 16px;
    border: none;
    border-radius: 6px;
    cursor: pointer;
    font-weight: 500;
    transition: background-color 0.3s ease-in-out, transform 0.2s;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    outline: none;
  }
  
  button:hover {
    background-color: #ddd;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  }
  
  button:active {
    transform: scale(0.96);
  }
  
  .flat {
    background-color: transparent;
    color: #42b983;
    border: 1px solid #42b983;
  }
  
  .flat:hover {
    background-color: #f0f9f5;
  }
  </style>