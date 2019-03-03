<template lang="pug">
  div.home
    h1 {{greetText}}
    h3 {{greetCount}}回目
    p(v-if="isRegulars") さんきゅー!
    p
      MyButton(:greet="greetText" @clicked="onMyButtonClicked") 挨拶するぜ
    p
      ResetButton( v-model="greetText" @clicked="resetCount")

</template>

<script lang="ts">
  import {Component, Vue, Watch} from "vue-property-decorator";
import MyButton from '@/components/MyButton.vue';
import ResetButton from '@/components/ResetButton.vue';

@Component({
  components: {
    ResetButton,
    MyButton,
  },
})
export default class Home extends Vue {
  public greetText: string = "Hello";

  private greetCount: number = 0;
  private worldGreetings: string[]  = Array.of("こんにちは", "Hello", "おはよう", "Good morning", "おやすみ", "Good night");

  public onMyButtonClicked() {
    this.greetText = this.randomWords();
    this.greetCount += 1;
  }

  public get isRegulars(): boolean {
    return this.greetCount >= 5 && this.greetCount <= 10
  }

  @Watch('greetCount')
  public countChange() {
    if(this.greetCount === 5) {
      alert('常連になりました');
    }
  }

  private randomWords(): string {
    return this.worldGreetings[Math.floor(Math.random() * this.worldGreetings.length)];
  }

  private resetCount() {
    this.greetCount = 0;
  }
}
</script>
