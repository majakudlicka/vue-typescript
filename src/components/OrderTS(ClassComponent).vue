<template>
  <div>
    <h3>{{ msg }}</h3>
    <div>{{order.productName}} </div>
    <div> has quantity of {{ order.quantity }} </div>
    <div> which is <b>{{isAboveThreshold}}</b></div>
    <div>
      <button @click="increment()">INCREASE Order Quantity</button>
      <br>
      <button @click="decrement()">DECREASE Order Quantity</button>
    </div>
  </div>
</template>


<script lang="ts">
 //  Lang="ts"
import { Component, Prop, Watch, Vue } from 'vue-property-decorator';
import { Order } from '../lib/types';

// Use of @Component decorator
@Component
//  We export class instead of object
export default class OrderTS extends Vue {

    // Props are declared using @Prop decorator
  @Prop({ default: 'default value' }) private msg!: string;

  @Prop({type: Object as () => Order}) private order!: Order;

  //  Data is declared as instance properties
  private bucketThreshold: number = 15;

  // Methods are declared as instance methods
  public increment(): void { this.order.quantity++; }
  public decrement(): void { this.order.quantity--; }

  // Lifecycle hooks
  public created(): void {
      console.log('TS: Hello from created hook!');
  }

  // Watchers are replaced with @Watch decorator
  @Watch('order', { immediate: true, deep: true })
  onMessageChanged(val: Order) {
      console.log(`Watcher TS: Order quantity is ${val.quantity}`);
  }

  // Computed props are defined as getters
  get isAboveThreshold(): string {
        return (this.order.quantity < this. bucketThreshold) ? 'below bucket threshold' : 'above bucket threshold';
  }
}
</script>

<style scoped>

h3 {
  margin: 40px 0 0;
}

</style>
