<template lang="pug">
  button(@click="onClick") Greet
</template>
<script lang="ts">
  import {Component, Emit, Prop, Vue} from "vue-property-decorator";

  @Component
  export default class MyButton extends Vue {
    private count: number = 0;

    @Prop()
    public greet?: string;

    @Emit()
    public clicked(count: number){
    }

    public onClick() {
      this.count++;
      this.clicked(this.count);
    }
  }
</script>

<style scoped>

</style>
