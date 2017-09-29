<template>
  <div class="container">
    <div class="picture"></div>
    <div class="content">
      <div class="navigator">
        <button class="button" @click="login=true" :class="{selected: login}">Log In</button>
        <button class="button" @click="login=false" :class="{selected: !login}">Sign Up</button>
      </div>
      <img src="https://upload.wikimedia.org/wikipedia/ru/6/65/Chess.com_logo.png" alt="chess board">      
      <transition name="fade">
        <form v-if="login">
          <h1>Log in to Your Account</h1>
          <input type="text" placeholder="Username">
          <input type="text" placeholder="Password">
          <input type="checkbox" id="rememberMe" name="rememberMe" value="rememberMe">
          <label for="rememberMe">Remember me</label>
          <a href="#">Forgot your password?</a>
          <input type="submit">
        </form>
      </transition>
      <transition name="fade">
        <div v-if="!login">
          <h1>Sign Up</h1>
          <input v-model="userData.username" type="text" placeholder="Username">
          <input v-model="userData.password" type="text" placeholder="Password">
          <input v-model="userData.confirmPassword" type="text" placeholder="Repeat Password">
          <p v-for="(message, i) in messages" :key="i" :style="{color: message[1]}">
            {{ message[0] }}
          </p>
          <input type="submit">
        </div>
      </transition>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      userData: {
        username: '',
        password: '',
        confirmPassword: '',
      },
      login: true,
    };
  },
  computed: {
    messages() {
      const messages = [];
      if (this.userData.password.length < 6 && this.userData.password !== '') {
        messages.push(['Your password must contain at least 6 characters', 'orange']);
      }
      if (this.userData.password !== this.userData.confirmPassword
        && this.userData.confirmPassword !== ''
        && this.userData.passWord !== ''
      ) {
        messages.push(['Your passwords do not match', 'red']);
      }
      return messages;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  margin-top: 12%;
  font-weight: normal;
  text-align: center;
}

img {
  width: 13%;
  float: right;
  margin-right: 5%;
  margin-top: 2%;
}

a {
  margin-left: 90px;
  color: #42b983;
  
}

.container {
  height: 550px;
  width: 1000px;
  margin: auto;
  -webkit-box-shadow: 6px 10px 37px 1px rgba(0, 0, 0, 0.57);
  -moz-box-shadow: 6px 10px 37px 1px rgba(0, 0, 0, 0.57);
  box-shadow: 6px 10px 37px 1px rgba(0, 0, 0, 0.57);
  border-radius: 0.3em;
  display: flex;
}

.picture {
  width: 40%;
  height: 100%;
  order: 1;
  background-image: url("https://www.chess.com/dynboard?fen=4rk2/5pqp/1p3N2/2p5/2P2Q2/P3P2P/6PK/8&size=2");
}

.content {
  width: 60%;
  height: 100%;
  order: 2;
  background-color: rgb(252, 249, 239);
}

.button {
  cursor: pointer;
  height: 35px;
  font-size: 20px;
  color: #2c3e50;
  border: none;
  flex-grow: 1;
  background-color: rgb(242, 239, 229);
}

.button:focus {
  outline: none;
}

.button:hover {
  font-size: 22px;
}

.navigator {
  display: flex;
  flex-flow: row;
}

p {
  text-align: center;
}

input[type="text"] {
  margin: 5% auto;
  display: block;
  width: 300px;
  height: 30px;
  border: 1px solid rgb(70, 66, 64);
  background-color: rgb(252, 249, 239);
  padding-left: 3%;
}

input[type="submit"] {
  margin: 5% auto;
  display: block;
  background-color: rgb(120, 106, 114);
  color: white;
  border: none;
  border-radius: 10px;
  width: 50%;
  height: 40px;
  font-size: 20px;
  font-family: 'Helvetica';
  font-weight: 400;
  -webkit-box-shadow: 3px 3px 13px 1px rgba(0, 0, 0, 0.57);
  -moz-box-shadow: 3px 3px 13px 1px rgba(0, 0, 0, 0.57);
  box-shadow: 3px 3px 13px 1px rgba(0, 0, 0, 0.57);
  cursor: pointer;
}

input[type="submit"]:hover {
  background-color: rgb(110, 96, 104);
}

input[type="checkbox"] {
  margin: 6% 0 0 18%;
}

.selected {
  background-color: rgb(252, 249, 239);
  color: #42b983;
}

.fade-enter {
  opacity: 0;
}

.fade-enter-active {
  transition: opacity 1s;
}
</style>
