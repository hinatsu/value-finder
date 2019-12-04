<template>
  <div >
    <div class="col-12">

      <draggable
        :list="listCloud" group="values"
        :key="lIndex"
      >
        <div v-for="(item, index) in listCloud" :key="index">{{ item }}</div>
      </draggable>
    </div>
    <div class="row">

    <div class="col-4">
      <draggable :list="listCrutial" group="values">
        <div v-for="(item, index) in listCrutial" :key="index">{{ item }}</div>
      </draggable>
    </div>
    <div class="col-4">
      <draggable :list="listImportant" group="values">
        <div v-for="(item, index) in listImportant" :key="index">{{ item }}</div>
      </draggable>
    </div>
    <div class="col-4"> 
      <draggable :list="listNormal" group="values">
        <div v-for="(item, index) in listNormal" :key="index">{{ item }}</div>
      </draggable>
    </div>
    </div>
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
      listCloud: [
        
          "honest",
          "romance",
          "change",
          "existense",
          "self-awareness",
          "discovery",
          "imagination","impact", "creation", "extraordinary","victory", "innovation", "future", "observant"
        
      ],
        listCrutial: [],
        listImportant:[],
        listNormal: []
    };
  }, // data

  methods: {
  }
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
  }
}
</style>
