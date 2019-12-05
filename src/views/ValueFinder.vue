<template>
  <div v-if="lists">
    <div class="col-12" v-if="lists.listCloud">
      <draggable :list="lists.listCloud" group="values">
        <span class="value-cloud" v-for="(value, index) in lists.listCloud" :key="index">{{ value.ja }}</span>
      </draggable>
    </div>
    <div class="row">
      <div id="important" class="col-4" v-if="lists.listImportant">
        <span>重要な価値観</span>
        <draggable :list="lists.listImportant" group="values">
          <span class="value-important" v-for="(value, index) in lists.listImportant" :key="index">
           
            {{ value.ja }}
          </span>
        </draggable>
      </div>
      <div id="crutial" class="col-4" v-if="lists.listCrutial">
        <span>最も重要な価値観</span>
        <draggable :list="lists.listCrutial" group="values">
          <div class="value-crutial" v-for="(value, index) in lists.listCrutial" :key="index">
            <span class="ranking" v-if="index === 0">
              <i class="fas fa-crown"></i>
              
            </span>
            <span class="ranking" v-else>{{index + 1}}</span>
            <span>{{ value.ja }}</span>
          </div>
        </draggable>
      </div>
      <div id="normal" class="col-4" v-if="lists.listNormal">
        <span>普通の価値観</span>
        <draggable :list="lists.listNormal" group="values">
          <span class="value-normal" v-for="(value, index) in lists.listNormal" :key="index">{{ value.ja }}</span>
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
    const savedList: string | null = localStorage.getItem('value-lists');

    if (savedList) {
      this.lists = JSON.parse(savedList);
    } else {
      this.lists.listCloud = VALUES;
    }
  }, // mounted

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
    background-color: white;
    min-height: 400px;
    width: 100%;
    margin: 10px;
    padding: 15px;
    border-radius: 10px;
    // box-shadow:
    > div {
      height: 100%;
      width: 100%;
    }
  }
}

.ranking {
  float: left;
  position: relative;
}

.value {
  &-cloud,
  &-crutial,
  &-important,
  &-normal {
    margin: 5px;

    &:hover {
      cursor: move;
    }
  }

  &-cloud {
    margin: 5px;
  }
}
</style>
