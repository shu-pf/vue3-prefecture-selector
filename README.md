# vue3-prefecture-selector

都道府県選択を簡単に行う為のモーダルコンポーネントです。

## DEMO

![デモ動画](https://user-images.githubusercontent.com/61904065/146673596-efc7c5c9-eca3-4b5f-8ebf-ee77f1c43e5c.gif)

[Codesandbox](https://codesandbox.io/s/vue3-prefecture-selector-demo-6od13)

## Features

都道府県選択を行う為のモーダルコンポーネントです。

地図上で、都道府県やテキストをクリックすることでイベントが発行されます。

## Requirement

- vue 3

## Installation

```bash
$ npm install vue3-prefecture-selector
```

## Usage

```vue
<template>
  <PrefectureSelector
    :visibility="visibility"
    @prefectureClick="onPrefectureClick"
    @close="closeModal"
  />
  <input type="text" v-model="inputValue" />
  <button @click="openModal">都道府県を選択する</button>
</template>

<script>
import PrefectureSelector from "prefecture-selector";

export default {
  name: "App",
  data() {
    return {
      visibility: false,
      inputValue: "未選択",
    };
  },
  components: {
    PrefectureSelector,
  },
  methods: {
    openModal() {
      this.visibility = true;
    },
    closeModal() {
      this.visibility = false;
    },
    onPrefectureClick(e) {
      this.inputValue = e.prefectureName;
      this.visibility = false;
    },
  },
};
</script>
```

## Spec

### Props

| 値         | 必須 | 型      | 説明                                                        |
| ---------- | ---- | ------- | ----------------------------------------------------------- |
| visibility | ○    | Boolean | モーダルウィンドウの表示(true)・非表示(false)を指定します。 |

### Event

| 値              | 返り値                     | 説明                                                             |
| --------------- | -------------------------- | ---------------------------------------------------------------- |
| prefectureClick | { prefectureName: string } | 都道府県がクリックされた時に発行されます。                       |
| close           | なし                       | モーダルウィンドウ内でクローズボタンが押された時に発行されます。 |

## License

"vue3-prefecture-selector" is under [MIT license](https://en.wikipedia.org/wiki/MIT_License).
