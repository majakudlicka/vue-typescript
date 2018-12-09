<template>
  <div id="app">
    <OrderTS msg="Simple Order App in TS using classes" :order="exampleOrder" />
    <br>
    <OrderJS msg="Simple Order App in JS" :order="exampleOrder"></OrderJS>
    <OrderTS2 msg="Simple Order App in TS using Vue.extend" :order="exampleOrder"></OrderTS2>
  </div>
</template>



<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import { Order } from './lib/types';
import OrderTS from './components/OrderTS(ClassComponent).vue';
import OrderJS from './components/OrderJS.vue';
import OrderTS2 from './components/OrderTS2(NoDecorators).vue';

@Component({
    // Components are declared inside @Component decorator
  components: {
    OrderTS,
    OrderJS,
    OrderTS2,
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
