<script lang="ts">
import { defineComponent } from 'vue';
import PrefectureSelector from '@/prefecture-selector.vue';

export default defineComponent({
  name: 'ServeDev',
  components: {
    PrefectureSelector
  }
});
</script>

<template>
  <div id="app">
    <prefecture-selector />
  </div>
</template>
