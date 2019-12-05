<template>
  <div>
    <div class="col-12">
      <draggable :list="listCloud" group="values" :key="lIndex">
        <span
          class="value-cloud"
          v-for="(value, index) in listCloud"
          :key="index"
          >{{ value.ja }}</span
        >
      </draggable>
    </div>
    <div class="row">
      <div class="col-4">
        <draggable :list="listCrutial" group="values">
          <div
            class="value-crutial"
            v-for="(value, index) in listCrutial"
            :key="index"
          >
            {{ value.ja }}
          </div>
        </draggable>
      </div>
      <div class="col-4">
        <draggable :list="listImportant" group="values">
          <div
            class="value-important"
            v-for="(value, index) in listImportant"
            :key="index"
          >
            {{ value.ja }}
          </div>
        </draggable>
      </div>
      <div class="col-4">
        <draggable :list="listNormal" group="values">
          <div
            class="value-normal"
            v-for="(value, index) in listNormal"
            :key="index"
          >
            {{ value.ja }}
          </div>
        </draggable>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { VALUES } from "@/constants";
const draggable = require("vuedraggable");

export default {
  components: {
    draggable
  },

  data() {
    return {
      listCloud: VALUES,
      listCrutial: [],
      listImportant: [],
      listNormal: []
    };
  }, // data

  methods: {} // methods
};
</script>

<style lang="scss" scoped>
.row {
  .col-12 {
    background-color: grey;
  }
  display: flex;
  flex-direction: row;
  .col-4 {
    background-color: grey;
    min-height: 400px;
    width: 100%;
    > div {
      height: 100%;
      width: 100%;
    }
  }
}

.value {
  &-cloud,
  &-crutial,
  &-important,
  &-normal {
    &:hover {
      cursor: move;
    }
  }

  &-cloud {
    margin: 5px;
  }
}
</style>
