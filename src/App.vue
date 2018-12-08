<template>
  <div id="app">
    <OrderTS msg="Simple Order App" :order="exampleOrder" />
  </div>
</template>



<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import OrderTS from './components/OrderTS.vue';

interface Order {
    productName: string;
    quantity: number;
}

@Component({
    // Components are declared inside @Component decorator
  components: {
    OrderTS,
  },
    // It is also a place where we could declare Vuex's binding helpers if using vuex
})
export default class App extends Vue {
    exampleOrder: Order = { productName: 'Poster', quantity: 10};
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
