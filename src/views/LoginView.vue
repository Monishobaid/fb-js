<template>
	<main class="login">
		<section class="forms">

			<form class="register" @submit.prevent="register">
				<h2>Register</h2>
				<input 
					type="email" 
					placeholder="Email address"
					v-model="register_form.email" />
				<input 
					type="password" 
					placeholder="Password" 
					v-model="register_form.password" />
				<input 
					type="submit" 
					value="Register" />
			</form>

			<form class="login-1" @submit.prevent="login">
				<h2>Login</h2>
				<input 
					type="email" 
					placeholder="Email address"
					v-model="login_form.email" />
				<input 
					type="password" 
					placeholder="Password" 
					v-model="login_form.password" />
				<input 
					type="submit" 
					value="Login" />
			</form>

		</section>
	</main>
</template>

<script>
import { ref } from 'vue'
import { useStore } from 'vuex'

export default {
	setup () {
		const login_form = ref({});
		const register_form = ref({});
		const store = useStore();

		const login = () => {
			store.dispatch('login', login_form.value);
		}

		const register = () => {
			store.dispatch('register', register_form.value);
		}

		return {
			login_form,
			register_form,
			login,
			register
		}
	}
}
</script>

<style scoped>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html,body {
  font-family: Arial, sans-serif;
  background-color: #3fec78;
}

.login {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color: white;
}

.forms {
  display: flex;
  flex-direction: column;
  gap: 220px;
  background-color: #ffffff;
  border-radius: 10px;
  padding: 30px;
}

.register,
.login-1 {
  display: flex;
  flex-direction: column;
  gap: 30px;
  box-shadow: 0px 30px 30px rgba(57, 75, 1, 0.1);
  padding: 40px;
  border-radius: 15px 50px 30px;
  background-color: #baf290;
}


input[type="email"],
input[type="password"],
input[type="submit"] {
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  font-size: 14px;
}

input[type="submit"] {
  background-color: #236f02;
  color: #fff;
  cursor: pointer;
  transition: background-color 0.3s;
}

input[type="submit"]:hover {
  background-color: #0056b3;
}

@media (min-width: 768px) {
  .forms {
    flex-direction: row;
  }

  .register,
  .login-1 {
    flex: 1;
  }
}

</style>
