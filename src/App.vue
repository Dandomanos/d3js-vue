<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link>|
      <router-link to="/colors">Colors</router-link>
    </div>
    <router-view class="container" />
  </div>
</template>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
  a {
    font-weight: bold;
    color: #2c3e50;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
.container {
  width: 100%;
  max-width: 800px;
  margin: 0 auto;
}
button {
  padding: 1rem;
  border-radius: 7px;
  background-color: cornflowerblue;
  color: white;
  text-transform: uppercase;
  border: 0;
  font-weight: bold;
  margin: 0 0.5rem;
  transition: background-color 1s;
  cursor: pointer;
  &:hover {
    background-color: darkgreen;
  }
  &:focus {
    outline: none;
    box-shadow: none;
  }
}
</style>
