<template lang="pug">
  button(@click="onClick") Reset
</template>

<script lang="ts">
  import {Component, Emit, Prop, Vue} from "vue-property-decorator";

  @Component
  export default class ResetButton extends Vue {
    private initialValue!: string;

    @Prop()
    public value!: string;

    @Emit()
    public input(value: string){
    }

    @Emit('clicked')
    public onClick() {
      this.input(this.initialValue);
    }

    public created() {
      this.initialValue = this.value
    }
  }
</script>

<style scoped>

</style>
