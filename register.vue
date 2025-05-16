<template>
  <div class="register-container">
    <h2>註冊新帳號</h2>
    <form @submit.prevent="handleRegister">
      <div class="form-group">
        <label for="name">姓名：</label>
        <input type="text" v-model="name" required />
      </div>

      <div class="form-group">
        <label for="email">電子郵件：</label>
        <input type="email" v-model="email" required />
      </div>

      <div class="form-group">
        <label for="password">密碼：</label>
        <input type="password" v-model="password" required />
      </div>

      <button type="submit">註冊</button>

      <p v-if="errorMessage" class="error">{{ errorMessage }}</p>
    </form>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'RegisterPage',
  data() {
    return {
      name: '',
      email: '',
      password: '',
      errorMessage: ''
    }
  },
  methods: {
    async handleRegister() {
      try {
        const response = await axios.post('/api/register.php', {
          name: this.name,
          email: this.email,
          password: this.password
        });

        if (response.data.success) {
          localStorage.setItem('access_token', response.data.access_token);
          localStorage.setItem('refresh_token', response.data.refresh_token);
          this.$router.push('/dashboard');
        } else {
          this.errorMessage = response.data.message || '註冊失敗';
        }
      } catch (error) {
        this.errorMessage = '伺服器錯誤，請稍後再試';
        console.error(error);
      }
    }
  }
}
</script>

<style scoped>
.register-container {
  max-width: 400px;
  margin: 50px auto;
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 6px;
  background-color: #fdfdfd;
}
.form-group {
  margin-bottom: 15px;
}
label {
  display: block;
  margin-bottom: 6px;
  font-weight: bold;
}
input[type="text"],
input[type="email"],
input[type="password"] {
  width: 100%;
  padding: 8px;
  box-sizing: border-box;
}
button {
  width: 100%;
  padding: 10px;
  background-color: #1dbf73;
  color: white;
  border: none;
  border-radius: 4px;
  font-weight: bold;
  cursor: pointer;
}
.error {
  color: red;
  margin-top: 10px;
}
</style>
