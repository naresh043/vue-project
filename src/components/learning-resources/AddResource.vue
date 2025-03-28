<template>
    <base-card>
      <h2>Add Resource</h2>
      <form @submit.prevent="submitResource">
        <div>
          <label>Title</label>
          <input type="text" v-model="title" required />
        </div>
        <div>
          <label>Description</label>
          <textarea v-model="description" required></textarea>
        </div>
        <div>
          <label>Link</label>
          <input type="url" v-model="link" required />
        </div>
        <base-button type="submit">Add Resource</base-button>
      </form>
    </base-card>
  </template>
  
  <script>
  export default {
    data() {
      return {
        title: "",
        description: "",
        link: ""
      };
    },
    methods: {
      submitResource() {
        // This would normally emit to parent or use a store
        alert("Resource added! (Implementation pending)");
        this.title = "";
        this.description = "";
        this.link = "";
      }
    }
  };
  </script>
  
  <style scoped>
  form div {
    margin: 1rem 0;
  }
  
  label {
    display: block;
    margin-bottom: 0.5rem;
    font-weight: bold;
  }
  
  input,
  textarea {
    width: 100%;
    padding: 0.5rem;
    border: 1px solid #ccc;
    border-radius: 4px;
    font-family: inherit;
  }
  </style>