<template>
  <div class="login-container">
    <h2>登入系統</h2>
    <form @submit.prevent="handleLogin">
      <div class="form-group">
        <label for="email">電子郵件：</label>
        <input type="email" v-model="email" required />
      </div>

      <div class="form-group">
        <label for="password">密碼：</label>
        <input type="password" v-model="password" required />
      </div>

      <button type="submit">登入</button>

      <p v-if="errorMessage" class="error">{{ errorMessage }}</p>
    </form>
  </div>
</template>


<script>
import axios from 'axios'

export default {
  name: 'LoginPage',
  data() {
    return {
      email: '',
      password: '',
      errorMessage: ''
    }
  },
  methods: {
    async handleLogin() {
      try {
        const response = await axios.post('/api/login.php', {
          email: this.email,
          password: this.password
        });

        if (response.data.success) {
          localStorage.setItem('access_token', response.data.access_token);
          localStorage.setItem('refresh_token', response.data.refresh_token);
          // 可選：跳轉至 dashboard 或主頁
          this.$router.push('/dashboard');
        } else {
          this.errorMessage = response.data.message || '登入失敗';
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
.login-container {
  max-width: 400px;
  margin: 50px auto;
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 6px;
  background-color: #f9f9f9;
}
.form-group {
  margin-bottom: 15px;
}
label {
  display: block;
  margin-bottom: 6px;
  font-weight: bold;
}
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
