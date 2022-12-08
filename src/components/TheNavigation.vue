<template>
  <!-- navigation bar -->
  <nav id="nav">
    <!-- logo -->
    <div class="logo">
      <router-link to="/about" class="logo"> </router-link>
    </div>
    <div class="nav-bar">
      <!-- navigation links -->
      <ul>
        <router-link to="/">Home</router-link>
        <router-link to="/about">About</router-link>
        <router-link to="#">Contact</router-link>
      </ul>
    </div>
  </nav>
</template>

<style scoped>
#nav {
  display: flex;
  align-items: center;
  position: sticky;
  top: 0;
  background-color: rgb(252, 252, 252);
  border-bottom: 1px solid grey;
  z-index: 1;
  justify-content: space-between;
}
#nav a {
  color: #2c3e50;
  text-decoration: none;
  font-weight: bold;
  margin-right: 50px;
}
ul {
  display: flex;
  list-style: none;
  margin-right: 40px;
}
#nav a.vue-school-active-class {
  color: #ab26ab;
}
.nav-links {
  display: flex;
}
.links {
  padding-right: 20px;
  list-style: none;
}
.links:hover {
  text-decoration: underline;
}
nav a.router-link-exact-active {
  color: #42b983;
}
.logo {
  margin-left: 40px;
  width: 120px;
  height: 50px;
  /* background image that is able to fit in the width and height */
  background: url("./../assets/images/manora_logo.jpg");
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}
</style>
