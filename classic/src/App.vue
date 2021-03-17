<template>
  <div>
    <img alt="Vue logo" src="./assets/logo.png" />
    <ul>
      <li v-for="item in menuItems" :key="item.id">
        {{ item.title }}
      </li>
    </ul>
    <ders @emittedData="inComingData($event)" />
  </div>
</template>

<script>
import Ders from "./components/Ders.vue";

export default {
  name: "App",
  components: {
    Ders,
  },
  data() {
    return {
      menuItems: null,
    };
  },
  methods : {
    inComingData(data){
      this.menuItems = data
    }
  }
  
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
