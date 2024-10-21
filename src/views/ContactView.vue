<template>
  <div class="pt-5 mt-5 contact-form">
    <h2>Contacto</h2>
    <form @submit.prevent="submitForm">
      <div class="form-group">
        <label for="name">Nombre:</label>
        <input
          type="text"
          id="name"
          v-model="form.name"
          required
          :class="{ 'is-invalid': errors.name }"
        />
        <span v-if="errors.name" class="error-message">{{ errors.name }}</span>
      </div>

      <div class="form-group">
        <label for="email">Email:</label>
        <input
          type="email"
          id="email"
          v-model="form.email"
          required
          :class="{ 'is-invalid': errors.email }"
        />
        <span v-if="errors.email" class="error-message">{{ errors.email }}</span>
      </div>

      <div class="form-group">
        <label for="message">Mensaje:</label>
        <textarea
          id="message"
          v-model="form.message"
          required
          :class="{ 'is-invalid': errors.message }"
        ></textarea>
        <span v-if="errors.message" class="error-message">{{ errors.message }}</span>
      </div>

      <button type="submit">Enviar</button>
    </form>
    <router-link type="button" class="btn btn-primary back-to-home text-center mx-auto" to="/">
      Volver al Home
    </router-link>
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        name: '',
        email: '',
        message: ''
      },
      errors: {
        name: null,
        email: null,
        message: null
      }
    };
  },
  methods: {
    validateForm() {
      this.errors.name = this.form.name ? null : 'Name is required';
      const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      this.errors.email = emailPattern.test(this.form.email) ? null : 'Valid email is required';
      this.errors.message = this.form.message ? null : 'Message is required';
      return !this.errors.name && !this.errors.email && !this.errors.message;
    },
    submitForm() {
      if (this.validateForm()) {
        alert('Form submitted successfully!');
        // Reset form
        this.form.name = '';
        this.form.email = '';
        this.form.message = '';
      }
    }
  }
};
</script>

<style>
.contact-form {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 8px;
  background-color: #f9f9f9;
}

.form-group {
  margin-bottom: 15px;
}

label {
  display: block;
  margin-bottom: 5px;
}

input,
textarea {
  width: 100%;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}

textarea {
  resize: vertical;
  height: 100px;
}

.is-invalid {
  border-color: red;
}

.error-message {
  color: red;
  font-size: 0.85rem;
}

button {
  background-color: #007bff;
  color: white;
  padding: 10px 15px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}
</style>

