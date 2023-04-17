<template>
  <main-screen
    v-if="statusMask == 'default'"
    @onStart="onHandleBeforeStart($event)"
  />
  <interact-screen
    v-if="statusMask == 'match'"
    :cardContext="settings.cardContext"
  />
</template>
<script>
import MainScreen from "./components/MainScreen.vue";
import InteractScreen from "./components/InteractScreen.vue";
import { shuffled } from "./utils/array";
export default {
  name: "App",
  data() {
    return {
      settings: {
        totalOfBlocks: 0,
        cardContext: [],
        startedAt: null,
      },
      statusMask: "default",
    };
  },
  components: {
    MainScreen,
    InteractScreen,
  },
  methods: {
    onHandleBeforeStart(configs) {
      this.settings.totalOfBlocks = configs.totalOfBlocks;
      const firstCard = Array.from(
        { length: this.settings.totalOfBlocks / 2 },
        (_, i) => i + 1
      );
      console.log(firstCard);
      const secondCard = [...firstCard];
      const card = [...firstCard, ...secondCard];
      this.settings.cardContext = shuffled(shuffled(shuffled(shuffled(card))));
      this.settings.startedAt = new Date().getTime();

      this.statusMask = "match";
    },
  },
};
</script>
