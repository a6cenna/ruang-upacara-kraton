<script>
import { defineComponent, provide, ref, defineAsyncComponent } from 'vue';

const FrontView = defineAsyncComponent(() => import('../src/views/FrontView.vue'));
const RightView = defineAsyncComponent(() => import('../src/views/RightView.vue'));
const InsideView = defineAsyncComponent(() => import('../src/views/InsideView.vue'));

export default defineComponent({
  name: "App",
  components: {
    FrontView,
    RightView,
    InsideView
  },
  setup() {
    const activeView = ref(0);
    provide('activeView', activeView);

    return {
      activeView
    }
  }
})
</script>

<template>
  <FrontView v-if="activeView === 0" />
  <RightView v-else-if="activeView === 1" />
  <InsideView v-else-if="activeView===2"></InsideView>
</template>

<style scoped>
</style>
