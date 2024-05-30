<template>
    <div class="registration-container">
      <h2>User Registration</h2>
      <div v-if="errorMessage" class="error-message">{{ errorMessage }}</div>
      <form @submit.prevent="submitForm">
        <label for="username">firstname:</label>
        <input type="text" id="firstname" v-model="firstname" required>
        <label for="username">surname:</label>
        <input type="text" id="surname" v-model="surname" required>
        <label for="sername">Date_of_birth:</label>
        <input type="date" id="Date_of_birth" v-model="Date_of_birth" required>
        <label for="email">Email:</label>
        <input type="email" id="email" v-model="email" required>
        <label for="password">Password:</label>
        <input type="password" id="password" v-model="password" required>
        <button type="submit">Register</button>
      </form>
      <div class="login-link">
        Already have an account? <router-link to="/login">Login</router-link>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        firstname: '',
        surname: '',
        Date_of_birth: '',
        email: '',
        password: '',
        errorMessage: ''
      };
    },
    methods: {
      submitForm() {
        // Perform registration logic here
        // Make an API call to the backend to register the user
        // Example using axios:
        axios.post('/registration', {
          firstname: this.firstname,
          surname:this.surname,
          Date_of_birth:this.Date_of_birth,
          email: this.email,
          password: this.password
        })
        .then(response => {
          // Registration success handling
          this.firstname = '';
          this.surname = '';
          this.Date_of_birth = '';
          this.email = '';
          this.password = '';
          this.$router.push('/login');
        })
        .catch(error => {
          // Registration error handling
          this.errorMessage = 'Registration failed. Please try again.';
        });
      }
    }
  };
  </script>
  
  <style scoped>
  .registration-container {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    color: #333;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
  }
  
  .error-message {
    color: red;
    margin-bottom: 10px;
  }
  
  form {
    margin-top: 10px;
    background: #fff;
    padding: 20px;
    margin: 20px auto;
    width: 80%;
    max-width: 500px;
    box-shadow: 0 0 10px rgba(0,0,0,0.1);
  }
  
  label {
    margin-bottom: 5px;
  }
  
input[type="text"],
input[type="email"],
input[type="password"],
textarea {
    width: 100%;
    padding: 10px;
    margin-top: 10px;
    margin-bottom: 20px;
    border: 1px solid #ddd;
    border-radius: 4px;
    box-sizing: border-box;
}
  
  button {
    background-color: #007bff;
    color: #fff;
    padding: 10px 20px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    width: 100%;
    margin: 10px auto;
  }

  button:hover {
    background-color: #0056b3;
}
                                                                                                                                 
/* Headings */
h1, h2, h3, h4, h5, h6 {
    color: #333;
}
  
  .login-link {
    text-align: center;
  }

  /* General Styles */

                                                                                                                                 
a {
    color: #007bff;
    text-decoration: none;
}
                                                                                                                                 
/* Navigation Bar */
nav {
    background-color: #333;
    color: #fff;
    padding: 10px;
}
                                                                                                                                 
nav a {
    color: #fff;
    margin: 0 15px;
}
                                                                                                                                 
                                                                                                                                                                                                                                                          
/* Utility Classes */
.container {
    width: 90%;
    margin: auto;
    max-width: 1200px;
}
                                                                                                                                 
.text-center {
    text-align: center;
}
                                                                                                                                 
/* Responsive Design */
@media screen and (max-width: 768px) {
    nav {
        text-align: center;
    }
                                                                                                                                 
    form {
        width: 95%;
    }
}

h1 {
    text-align: center;
  }

  .additional-links {
    text-align: center;
  }
  
  .additional-links a {
    font-family: Arial, sans-serif;
    text-decoration: none;
    color: #007bff;
    margin-right: 10px;
  }
  
  .additional-links a:last-child {
    margin-right: 0;
  }
  </style>
  