<template>
  <main-screen
    v-if="statusMask == 'default'"
    @onStart="onHandleBeforeStart($event)"
  />
  <interact-screen v-if="statusMask == 'match'" />
</template>
<script>
import MainScreen from "./components/MainScreen.vue";
import InteractScreen from "./components/InteractScreen.vue";
export default {
  name: "App",
  data() {
    return {
      statusMask: "default",
    };
  },
  components: {
    MainScreen,
    InteractScreen,
  },
  methods: {
    onHandleBeforeStart(config) {
      console.log(config);
      this.statusMask = "match";
    },
  },
};
</script>
