<template>
  <div class="sreen">
    <div class="screen__inner">
      <CardFlip v-for="(card, index) in cardContext" :key="index" />
    </div>
  </div>
</template>

<script>
import CardFlip from "./Card.vue";
export default {
  props: {
    cardContext: {
      type: Array,
      default: function () {
        return [];
      },
    },
  },
  components: {
    CardFlip,
  },
};
</script>
<style scoped>
.screen {
  width: 100%;
  height: 100vh;
  position: absolute;
  top: 0;
  left: 0;
  z-index: 2;
  background-color: var(--dark);
  color: var(--light);
}

.screen__inner {
  width: calc(424px);
  display: flex;
  flex-wrap: wrap;
  margin: 2rem auto;
}
</style>
