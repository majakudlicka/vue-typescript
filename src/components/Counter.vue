<template>
  <div>
    <h3>{{ msg }}</h3>
    <div>{{count}} is {{isOdd}}</div>
    <div>
      <button @click="increment()">INCREMENT</button>
    </div>
  </div>
</template>


<script lang="ts">
 //  Lang="ts"
import { Component, Prop, Watch, Vue } from 'vue-property-decorator';

@Component
//  We export class instead of object
export default class Counter extends Vue {

    // Props are declared using @Prop decorator
  @Prop({ default: 'default value' }) private msg!: string;

  //  'Data' is declared as instance properties
  private count = 0;

  // Methods are declared as class functions
  public increment() { this.count++; }

  // Lifecycle hooks
  public created() {
      console.log('hello');
  }

  // Watchers are replaced with @Watch decorator
  @Watch('msg', { immediate: true })
  onMessageChanged(val: string, oldVal: string) {
      console.log(`New message is ${val}`);
  }

  // Computed props are defined as getters
  get isOdd() {
        return (this.count % 2 === 0) ? 'even' : 'odd';
  }
}
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
