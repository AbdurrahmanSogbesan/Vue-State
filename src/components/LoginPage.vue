<template>
  <div class="login">
    <center><h1>Login</h1></center>
    <form>
      <div class="container">
        <label>Username : </label>
        <input
          type="text"
          placeholder="Enter Username"
          v-model="login.userName"
          required
        />
        <label>Password : </label>
        <input
          type="password"
          placeholder="Enter Password"
          v-model="login.password"
          required
        />
        <button type="submit" @click="loginMsg">Login</button>
      </div>
    </form>
    <div class="verify">
      Username: {{ login.userName }} Password: {{ login.password }}
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      login: {
        userName: "",
        password: "",
      },
    };
  },
  props: {
    msg: String,
  },
  methods: {
    loginMsg() {
      alert(
        "You have sucessfully logged in " +
          this.login.userName +
          " with passsword " +
          this.login.password
      );
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.login {
  margin: 0 30%;
}
button {
  background-color: #4caf50;
  width: 100%;
  color: orange;
  padding: 15px;
  margin: 10px 0px;
  border: none;
  cursor: pointer;
  border-radius: 7px;
  font-size: 14px;
  font-weight: bold;
}
form {
  border: 3px solid #f1f1f1;
}
input[type="text"],
input[type="password"] {
  width: 100%;
  margin: 8px 0;
  padding: 12px 20px;
  display: inline-block;
  border: 2px solid green;
  box-sizing: border-box;
  border-radius: 7px;
}
button:hover {
  opacity: 0.7;
}

.container {
  padding: 25px;
  background-color: lightblue;
}
.verify {
  background: #ccc;
  margin: 30px 0;
  padding: 15px;
  border-radius: 7px;
}
</style>
