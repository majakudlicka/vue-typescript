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


<script>
    export default {
        props: {
            msg: {
                default: 'default value',
            },
            order: {
                type: Object,
            },
        },
        data: () => ({
            bucketThreshold: 15,
        }),
        methods: {
            increment() {
                return this.order.quantity++;
            },
            decrement() {
                return this.order.quantity--;
            },
        },
        created() {
            console.log('Hello from created hook in JS app!');
        },
        watch: {
            order: {
                handler(val) {
                    console.log(`Order quantity is ${val.quantity}`);
                },
                deep: true,
                immediate: true,
            },
        },
        computed: {
            isAboveThreshold() {
                return (this.order.quantity < this.bucketThreshold) ? 'below bucket threshold' : 'above bucket threshold';
            },
        },
    };
</script>

<style scoped>

    h3 {
        margin: 40px 0 0;
    }

</style>
