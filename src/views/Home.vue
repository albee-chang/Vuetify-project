<template>
  <VCalendar :attributes="attributes" />
  <TodoList />
</template>

<script lang="ts" setup>
import TodoList from '../components/TodoList.vue'
import { ref } from "vue";

const attributes = ref([
  {
    highlight: true,
    dates: {
      start: new Date(2023, 4, 7),
      repeat: {
        every: [2, "weeks"],
        weekdays: 0,
      },
    },
  },
]);

</script>
