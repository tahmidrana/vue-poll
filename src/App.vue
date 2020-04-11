<template>
  <div id="app">
    <div id="logo-area">
      <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
      <h1><router-link to="/">Vue Poll</router-link></h1>
    </div>
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link> |
      <router-link to="/new-poll">New</router-link> |
      <router-link to="/login">Login</router-link> |
      <router-link to="/register">Register</router-link>
    </div>
    <router-view/>
  </div>
</template>

<script>
export default {
  //
}
</script>

<style>
a, h1, h2, h3, h4, h5, h6 {
  color: #2c3e50;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  width: 800px;
  margin: 0 auto;
}

#logo-area{
  text-align: center;
}
#logo-area img{
  width: 65px;
}
.text-center {
  text-align: center;
}
#logo-area h1{
  margin: 0;
}
#logo-area h1 a{
  font-family: 'Pacifico', cursive;
  font-size: 40px;
  color: #2c3e50;
  text-decoration: none;
}

#nav {
  padding: 30px;
  text-align: center;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
  margin: 0 10px;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
.btn {
  border: 0;
  padding: 8px 14px;
  cursor: pointer;
  font-size: 14px;
  border-radius: 3px;
  font-weight: bold;
  display: block;
}
.btn-primary{
  color: #ffffff;
  background: #3574d4;
}
.btn-primary:hover{
  background: #2d67bf;
}
.btn-success{
  color: #ffffff;
  background: #42b983;
}
.btn-success:hover{
  background: #39a674;
}
.poll-title{
    margin: 10px 0;
    padding: 0;
}

.poll-feat{
    font-size: 14px;
    margin: 0;
    padding: 0;
}
.poll-author{
    color: #42b983;
}

.card{
  width: 100%;
  background-color: papayawhip;
  padding: 18px;
  box-shadow: 3px 3px 3px #eee;
}
.form-control {
    width: 100%;
    padding: 8px 12px;
    box-sizing: border-box;
}
.form-group{
  margin: 15px 0;
}
label {
  display: block;
}
.clearfix {
  overflow: auto;
}
.right{
  float: right;
}
</style>
