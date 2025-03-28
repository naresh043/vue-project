<template>
    <li>
      <base-card>
        <header>
          <h3>{{ title }}</h3>
          <base-button mode="flat">Delete</base-button>
        </header>
        <p>{{ description }}</p>
        <nav>
          <a :href="link" target="_blank">View Resource</a>
        </nav>
      </base-card>
    </li>
  </template>
  
  <script>
  export default {
    props: ["id", "title", "description", "link"]
  };
  </script>
  
  
  <style scoped>
  @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');
  
  li {
    list-style: none;
    margin: 1rem 0;
    padding: 1rem;
    border: 1px solid #ccc;
    border-radius: 8px;
    font-family: 'Roboto', sans-serif;
  }
  
  header {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  
  h3 {
    font-size: 1.5rem;
    color: #333;
  }
  
  button {
    background-color: #ff6b6b;
    color: white;
    border: none;
    padding: 0.5rem 1rem;
    border-radius: 4px;
    cursor: pointer;
  }
  
  button:hover {
    background-color: #ff4c4c;
  }
  
  p {
    margin: 0.5rem 0;
    color: #555;
  }
  
  a {
    color: #007bff;
    text-decoration: none;
  }
  
  a:hover {
    text-decoration: underline;
  }
  </style>
  