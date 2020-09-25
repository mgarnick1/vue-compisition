<template>
  <main>
    <h1>Count:</h1>
    <h3>{{ count }}</h3>
    <button @click="addToCount">Increase Count</button>
  </main>
</template>

<script lang="ts">
import {
  defineComponent,
  toRefs,
  reactive,
  watchEffect
} from "@vue/composition-api";

export default defineComponent({
  setup() {
    const state = reactive({
      count: 0
    })

    function addToCount() {
      state.count++;
    }

    watchEffect(() => {
      console.log(state.count);
    });

    return {
      ...toRefs(state),
      addToCount
    };
  }
});
</script>
