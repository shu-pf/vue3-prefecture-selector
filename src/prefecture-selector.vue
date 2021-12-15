<script lang="ts">
import { defineComponent } from "vue";
import PrefectureSvg from "./prefecture-svg.vue";

export default defineComponent({
  name: "PrefectureSelector",
  components: { PrefectureSvg },
});
</script>

<template>
  <div class="prefecture-selector">
    <PrefectureSvg />
  </div>
</template>

<style scoped></style>
