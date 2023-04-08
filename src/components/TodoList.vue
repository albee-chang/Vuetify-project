<template>
    <v-app>
    <v-toolbar>
      <v-toolbar-title>Todo List</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn>Button</v-btn>
    </v-toolbar>
    <v-container>
      <v-card v-for="(item, index) in items"
              :key="index"
              :class="{ 'completed': item.completed }">
        <v-card-title>{{ item.text }}</v-card-title>
        <v-card-text>Card Text</v-card-text>
        <v-card-actions>
          <v-btn icon color="blue" @click="()=>adjustItem(index)"><v-icon icon="mdi-wrench"></v-icon> 修改</v-btn>
          <v-btn icon color="red" @click="() => deleteItem(index)"><v-icon>mdi-delete</v-icon>刪除</v-btn>
        </v-card-actions>
      </v-card>
    </v-container>
    <v-card-actions>
          <v-text-field v-model="newItem" label="New Item"></v-text-field>
          <v-btn color="primary" @click="addItem">Add</v-btn>
        </v-card-actions>
  </v-app>
  </template>
  
  <script lang="ts">
  import { defineComponent } from 'vue'
  
  export default defineComponent({
    name: 'TodoList',
    data() {
      return {
        items: [
          { text: 'Item 1', completed: false },
          { text: 'Item 2', completed: true },
        ],
        newItem: '',
      }
    },
    methods: {
      //Generate a function to add a new item to the list
      addItem() {
        this.items.push({ text: this.newItem, completed: false })
        this.newItem = ''
      },
      //Generate a function to delete the item at the given index
      deleteItem(index: number) {
        this.items.splice(index, 1)
      },
      //Generate a function to adjust the item at the given index    
      adjustItem(index: number) {
        this.items[index].text = this.newItem
        this.newItem = ''
      },
    },
  })
  </script>
  