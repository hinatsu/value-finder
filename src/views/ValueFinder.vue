<template>
  <div v-if="lists">
    <div class="col-12" v-if="lists.listCloud">
      <draggable :list="lists.listCloud" group="values">
        <span class="value-cloud" v-for="(value, index) in lists.listCloud" :key="index">{{ value.ja }}</span>
      </draggable>
    </div>
    <div class="row">
      <div id="crutial" class="col-4" v-if="lists.listCrutial">
        <draggable :list="lists.listCrutial" group="values">
          <div class="value-crutial" v-for="(value, index) in lists.listCrutial" :key="index">{{ value.ja }}</div>
        </draggable>
      </div>
      <div id="important" class="col-4" v-if="lists.listImportant">
        <draggable :list="lists.listImportant" group="values">
          <div class="value-important" v-for="(value, index) in lists.listImportant" :key="index">{{ value.ja }}</div>
        </draggable>
      </div>
      <div id="normal" class="col-4" v-if="lists.listNormal">
        <draggable :list="lists.listNormal" group="values">
          <div class="value-normal" v-for="(value, index) in lists.listNormal" :key="index">{{ value.ja }}</div>
        </draggable>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { VALUES } from '@/constants';
const draggable = require('vuedraggable');

export default {
  components: {
    draggable
  },

  data() {
    return {
      values: VALUES,
      lists: {
        listCloud: [] as any[],
        listCrutial: [] as any[],
        listImportant: [] as any[],
        listNormal: [] as any[]
      } as any
    };
  }, // data

  watch: {
    lists: {
      // eslint-disable-next-line
      handler: function() {
        localStorage.setItem('value-lists', JSON.stringify(this.lists));
      },
      deep: true
    }
  },

  mounted() {
    const savedList = localStorage.getItem('value-lists');

    if (savedList) {
      this.lists = JSON.parse(savedList);
    } else {
      this.lists.listCloud = VALUES;
    }
  },

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
  #crutial {
  }
  #important {
  }
  #normal {
  }
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
