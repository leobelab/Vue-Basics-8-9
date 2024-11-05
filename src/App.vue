<template>
  <div id="nav"><!--vue intercepts the request to server with router-link tag which swaps components rathering to send another request to the server-->
    <router-link to="/">Home</router-link> |
    <router-link :to="{name: 'about'}">About</router-link> |<!--to link the router link this way, with the name and not the path, if this path changes, we won't need to change anything-->
    <router-link :to="{name: 'jobs'}">Jobs</router-link> 
  </div>

  <button @click="redirect">Redirect</button>
  <button @click="back">Go back</button>
  <button @click="forward">Go forward</button>

  <router-view/>
</template>

<script>
export default {
  methods: {
    redirect() {
      this.$router.push({name: 'home'})
    },
    back() {//router to get information of the current route. We pass a - number or a + number(how many steps on the history)
      this.$router.go(-1)
    },
    forward() {
      this.$router.go(1)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
  text-decoration: none;
  padding: 10px;
  border-radius: 4px;
}

#nav a.router-link-exact-active {
  color: white;
  background: crimson;
}

button {
  margin: 0 10px;
  padding: 10px;
  border: none;
  border-radius: 4px;
}
</style>
