<template lang="pug">
  button(@click="onClick")
    slot
</template>
<script lang="ts">
  import {Component, Emit, Prop, Vue} from "vue-property-decorator";

  @Component
  export default class MyButton extends Vue {

    @Prop()
    public greet?: string;

    @Emit('clicked')
    public onClick() {
    }
  }
</script>

<style scoped>

</style>
