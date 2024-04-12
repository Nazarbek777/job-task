<template>
<div class="container mx-auto py-5">
  <div class="bg">
    <Tree id="my-tree-id" ref="my-tree-ref" :custom-options="myCustomOptions" :custom-styles="myCustomStyles" :nodes="treeDisplayData"></Tree>
  </div>
</div>
</template>

<script setup>
import { ref } from "vue";
import Tree from 'vuejs-tree'

const treeDisplayData = ref([
  {
    text: 'Root 1',
    state: { checked: false, selected: false, expanded: false },
    nodes: [
      {
        text: 'Child 1',
        state: { checked: false, selected: false, expanded: false },
        nodes: [
          {
            text: 'Grandchild 1',
            state: { checked: false, selected: false, expanded: false },
            nodes: [
              {
                text: 'Grandchild 4',
                state: { checked: false, selected: false, expanded: false }
              },
              {
                text: 'Grandchild 5',
                state: { checked: false, selected: false, expanded: false }
              }
            ]
          },

          {
            text: 'Grandchild 2',
            state: { checked: false, selected: false, expanded: false }
          }
        ]
      },
      {
        text: 'Child 2',
        state: { checked: false, selected: false, expanded: false }
      }
    ]
  },
  {
    text: 'Root 2',
    state: { checked: false, selected: false, expanded: false }
  }
]);

const myCustomOptions = ref({
  openedIcon: '+',
  closedIcon: '-'
});

const myCustomStyles = ref({
  treeNode: {
    color: 'red',
    'font-weight': 'bold'
  }
});


</script>

<style scoped>
.bg{
  background-color: #e8e2e2;
  width: 560px;
}

</style>

