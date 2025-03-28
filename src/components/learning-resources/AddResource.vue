<template>
  <base-card class="add-resource-container">
    <h2 class="form-title">Add Resource</h2>
    <form @submit.prevent="submitResource" class="resource-form">
      <div class="form-control">
        <label for="title">Title</label>
        <input id="title" type="text" v-model.trim="title"  />
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea id="description" v-model.trim="description" ></textarea>
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input id="link" type="url" v-model.trim="link"  />
      </div>
      <div class="form-actions">
        <base-button type="submit" class="submit-button">Add Resource</base-button>
      </div>
    </form>

    <base-dialog
      v-if="invalid"
      title="Invalid Input"
      @close="invalid = false"
    >
      <template #default>
        <p>Please enter valid values in all fields.</p>
        <p>All fields must be non-empty.</p>
      </template>
      <template #actions>
        <base-button @click="invalid = false">Okay</base-button>
      </template>
    </base-dialog>
  </base-card>
</template>

<script>
export default {
  data() {
    return {
      title: '',
      description: '',
      link: '',
      invalid: false
    };
  },
  methods: {
    submitResource() {
      if (this.title.trim() === '' || this.description.trim() === '' || this.link.trim() === '') {
        this.invalid = true;
        return;
      }

      this.addResource({
        title: this.title,
        description: this.description,
        link: this.link
      });

      // Reset form
      this.title = "";
      this.description = "";
      this.link = "";
    }
  },
  inject: ["addResource"]
};
</script>

<style scoped>
/* Base styles for all devices */
.add-resource-container {
  max-width: 100%;
  padding: 1.5rem;
  box-sizing: border-box;
}

.form-title {
  color: #2c3e50;
  text-align: center;
  margin-bottom: 2rem;
  font-size: 1.75rem;
}

.resource-form {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.form-control {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

label {
  font-weight: 600;
  color: #2c3e50;
  font-size: 1rem;
}

input,
textarea {
  width: 100%;
  padding: 0.75rem 1rem;
  border: 2px solid #e0e0e0;
  border-radius: 8px;
  font-size: 1rem;
  transition: all 0.3s ease;
  box-sizing: border-box;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #42b983;
  box-shadow: 0 0 0 3px rgba(66, 185, 131, 0.2);
}

textarea {
  min-height: 120px;
  resize: vertical;
}

.form-actions {
  display: flex;
  justify-content: center;
  margin-top: 1rem;
}

.submit-button {
  padding: 0.75rem 2rem;
  font-size: 1rem;
  background-color: #42b983;
  color: white;
  border: none;
}

.submit-button:hover {
  background-color: #3aa876;
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .add-resource-container {
    padding: 1rem;
    margin: 0.5rem;
  }

  .form-title {
    font-size: 1.5rem;
    margin-bottom: 1.5rem;
  }

  .resource-form {
    gap: 1.25rem;
  }

  input,
  textarea {
    padding: 0.65rem 0.9rem;
    font-size: 0.95rem;
  }

  .submit-button {
    padding: 0.65rem 1.75rem;
    width: 100%;
  }
}

@media (max-width: 480px) {
  .form-title {
    font-size: 1.3rem;
    margin-bottom: 1.25rem;
  }

  .resource-form {
    gap: 1rem;
  }

  label {
    font-size: 0.95rem;
  }

  input,
  textarea {
    padding: 0.6rem 0.8rem;
    font-size: 0.9rem;
  }

  textarea {
    min-height: 100px;
  }
}

/* Large screens */
@media (min-width: 1200px) {
  .add-resource-container {
    max-width: 800px;
    margin: 0 auto;
  }
}
</style>