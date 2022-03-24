<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld msg="Welcome to Your Vue.js + TypeScript App" />
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import HelloWorld from './components/HelloWorld.vue'

declare const google: any
export default defineComponent({
  name: 'App',
  components: {
    HelloWorld,
  },
  data: () => ({
    isSignedIn: false,
  }),
  mounted() {
    google.accounts.id.initialize({
      client_id: process.env.VUE_APP_CLIENT_ID,
      callback: (response: any) => {
        console.log(response)
      },
    })
    google.accounts.id.prompt()
  },
})
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
