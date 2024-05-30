
<template>
  <div class="container d-flex justify-content-center align-items-center vh-90" id="login">
    <div class="card shadow-lg p-5 rounded">
      <h3 class="alert alert-primary mt-2 d-flex justify-content-start" style="text-left">FREE-MAILING LOGIN</h3>
      <form @submit.prevent="login">
        <div class="mb-4 d-flex">
          <label class="flex-grow-1 form-label w-15" for="email">Email</label>
          <input class="flex-grow-4 form-control w-75"  type="email" id="email" v-model="email" required>
        </div>
        <div class="mb-4 d-flex">
          <label class="flex-grow-1 form-label w-15"  for="password">Password</label>
          <input class="flex-grow-4 form-control w-75"  type="password" id="password" v-model="password" required>
        </div>
        <button type="submit" class="btn btn-primary w-100">Login</button>
      </form>
      <div v-if="error" class="alert alert-danger mt-3" role="alert">
        {{ error }}
      </div>
      <div class="mt-3 text-center">
        Don't have an account? <a href="#" @click.prevent="showRegisterForm = true">Register</a>
      </div>
    </div>

    <div v-if="showRegisterForm" class="modal fade show" tabindex="-1" role="dialog" style="display: block; background-color: rgba(0, 0, 0, 0.5);">
      <div class="modal-dialog modal-dialog-centered" role="document" id="register">
        <div class="modal-content">
          <div class="modal-header">
            <h4 class="alert alert-primary d-flex justify-content-start" style="text-left">FREE-MAILING REGISTRATION</h4>
            <button type="button" class="btn btn-close" @click.prevent="showRegisterForm = false"></button>
          </div>
          <div class="modal-body">
            <form @submit.prevent="register">
              <div class="mb-3 d-flex">
                <label for="register-name" class="form-label flex-grow-1 w-15">Name</label>
                <input type="text" class="form-control flex-grow-3 w-75" style="width: 100%;" id="name" v-model="registerEmail" required>
              </div>
              <div class="mb-3 d-flex">
                <label for="register-surname" class="form-label flex-grow-1 w-15">Surname</label>
                <input type="text" class="form-control flex-grow-3 w-75" id="surname" v-model="registerEmail" required>
              </div>
              <div class="mb-3 d-flex">
                <label for="register-dob" class="form-label flex-grow-1 w-15">D.o.b</label>
                <input type="date" class="form-control flex-grow-3 w-75" id="dob" v-model="registerEmail" required>
              </div>
              <div class="mb-3 d-flex">
                <label for="register-email" class="form-label flex-grow-1 w-15">Email</label>
                <input type="email" class="form-control flex-grow-3 w-75" id="register-email" v-model="registerEmail" required>
              </div>
              <div class="mb-3 d-flex">
                <label for="register-password" class="form-label flex-grow-1 w-15">Password</label>
                <input type="password" class="form-control flex-grow-3 w-75" id="register-password" v-model="registerPassword" required>
              </div>
              <button type="submit" class="btn btn-primary w-100">Register</button>
            </form>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'LoginPage',
  data() {
    return {
      email: '',
      password: '',
      error: null,
      showRegisterForm: false,
      registerEmail: '',
      registerPassword: ''
    }
  },
  methods: {
    login() {
      // Add your login logic here
      if (this.email === 'test@example.com' && this.password === 'password') {
        // Successful login
        console.log('Logged in successfully');
      } else {
        this.error = 'Invalid email or password';
      }
    },
    register() {
      // Add your registration logic here
      console.log('Registered:', this.registerEmail, this.registerPassword);
      this.showRegisterForm = false;
    }
  }
}
</script>

<style scoped>

login{
 width: 100%;
}

register{
  width: 100%;
}

.vh-100 {
  height: 100vh;
}
</style>
