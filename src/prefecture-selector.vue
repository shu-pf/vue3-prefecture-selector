<script lang="ts">
import { defineComponent, SetupContext } from "vue";
import PrefectureSvg from "./prefecture-svg.vue";

export default defineComponent({
  name: "PrefectureSelector",
  props: {
    visibility: {
      type: Boolean,
      required: true,
    },
  },
  components: { PrefectureSvg },
  setup(_, context: SetupContext) {
    const onPrefectureClick = (e: { prefectureName: string }) => {
      context.emit("prefectureClick", e);
    };
    const close = () => {
      context.emit("close");
    };
    return {
      onPrefectureClick,
      close,
    };
  },
});
</script>

<template>
  <div class="container" :class="{ 'display-block': visibility }">
    <div class="overlay">
      <div class="content">
        <div>
          <PrefectureSvg @prefectureClick="onPrefectureClick" />
        </div>
        <div class="content__close">
          <a @click="close">x close</a>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: none;
}
.display-block {
  display: block;
}
.overlay {
  /*　要素を重ねた時の順番　*/
  z-index: 1;

  /*　画面全体を覆う設定　*/
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);

  /*　画面の中央に要素を表示させる設定　*/
  display: flex;
  align-items: center;
  justify-content: center;
}
.content {
  z-index: 2;
  width: 80%;
  padding: 1em;
  background: #fff;
  max-width: 560px;
}
.content__close {
  text-align: right;
  cursor: pointer;
}
</style>
