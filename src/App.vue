<template>
  <div class = 'container'>
    <Datatable :action = 'action' :data = 'data' />
  </div>

</template>

<script setup>
import Datatable from './components/CrudComponent.vue'
const data = [
  {
    name: 'Name',
    age: 'Age',
    address: 'Address',
    tags: 'Tags',
    action: 'Action',
  }
]

const action = [
  {
    id : 1,
    name : "Nazarbek",
    age : 32,
    address : 'Lorem ipsum',
    status : 'nice',
    job : 'fullstack',
  },
  {
    id : 2,
    name : "Jim ",
    age : 42,
    address : 'Lorem ipsum',
    status : 'loser',
    job : 'fullstack',
  },
  {
    id : 3,
    name : "Joe ",
    age : 32,
    address : 'Lorem ipsum',
    status : 'cool',
    job : 'fullstack',
  },
]







</script>