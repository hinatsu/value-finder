<template>
  <div>
    <draggable
      :options="{ group: 'values' }"
      element="ul"
      v-for="(list, lIndex) in values"
      :key="lIndex"
    >
      <li v-for="(item, index) in list" :key="index">{{ item }}</li>
    </draggable>
  </div>
</template>

<script lang="ts">
const draggable = require("vuedraggable");

export default {
  components: {
    draggable
  },
  data() {
    return {
      values: [
        [
          "honest",
          "romance",
          "change",
          "existense",
          "self-awareness",
          "discovery",
          "imagination"
        ],
        ["impact", "creation", "extraordinary"],
        ["victory", "innovation", "future", "observant"]
      ]
    };
  }
};
</script>

<style lang="scss" scoped></style>
