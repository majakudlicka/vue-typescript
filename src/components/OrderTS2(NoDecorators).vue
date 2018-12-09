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
    import Vue from 'vue';
    import { Order } from '../lib/types';

    export default Vue.extend({
        props: {
            msg: {
                default: 'default value',
                type: String,
            },
            order: {
                type: Object as () => Order,
            },
        },
        data: () => ({
            bucketThreshold: 15,
        }),
        methods: {
            increment(): number {
                return this.order.quantity++;
            },
            decrement(): number {
                return this.order.quantity--;
            },
        },
        created() {
            console.log('TS: Hello from created hook!');
        },
        watch: {
            order: {
                handler(val: Order): void {
                    console.log(`Watcher TS: Order quantity is ${val.quantity}`);
                },
                deep: true,
                immediate: true,
            },
        },
        computed: {
            isAboveThreshold(): string {
                return (this.order.quantity < this.bucketThreshold) ? 'below bucket threshold' : 'above bucket threshold';
            },
        },
    });
</script>

<style scoped>

    h3 {
        margin: 40px 0 0;
    }

</style>
