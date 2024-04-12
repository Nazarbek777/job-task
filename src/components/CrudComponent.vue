<template>
 <div class="container ">
  <div class="row">
    <div id="submit">
    </div>
   <div class="col-md-8">
     <table class="table  brd mt-3 ">
       <thead>
       <tr v-for="title in data">
         <th scope="col" width="150">{{title.name}}</th>
         <th scope="col" width="150">{{title.age}}</th>
         <th scope="col" width="150"> {{title.address}}</th>
         <th scope="col" width="150">{{title.tags}}</th>
         <th scope="col"  width="150">{{title.action}}</th>
       </tr>
       </thead>
       <tbody>
       <tr v-for="lime in action " >
         <td class="text" >{{lime.name}}</td>
         <td class="text" >{{lime.age}}</td>
         <td class="text" >{{lime.address}}</td>
         <td class="text-status text" width="150"><b>{{lime.status}}</b></td>
         <td  class="align-items-center  d-flex justify-content-around">
           <a class="btn-del" type="submit"><img width="20px"   src="./icons/images/delete.png" alt=""></a>
           <button class="btn"  type="submit" href="#" @click="handleEditClick(lime.id,lime.name,lime.age,lime.address,lime.status)">
             <img width="20px" class="" src="./icons/images/edit.png" alt="">
           </button>
           <button type="submit" class="btn" @click="viewItem(lime.id)"><img width="20px" src="./icons/images/eye.png" alt=""></button>
         </td>
       </tr>
       </tbody>

     </table>
   </div>
    <div id="show">
    </div>
    <form action="" @submit.prevent="handleSubmit" v-if="inSubmit">
      <input  v-model="selectedItemId" type="text" name="selectedItemId">
      <input v-model="selectedItemName" type="text" name="selectedItemId">
      <input v-model="selectedItemAge" type="text" name="selectedItemId">
      <input v-model="selectedItemAddress " type="text" name="selectedItemId">
      <input v-model="selectedItemStatus " type="text" name="selectedItemId">
      <button type="submit">submit</button>
    </form>
  </div>

 </div>
  <TreeComponent></TreeComponent>

</template>
<script setup>
import { defineProps, onMounted, ref } from "vue";
import TreeComponent from "@/components/TreeComponent.vue";
const { data, action } = defineProps(["data", "action"]);


const viewItem = (id) => {
  const selectedItem = action.find(item => item.id === id);
  const selectedItemString = JSON.stringify(selectedItem);
  const appElement = document.getElementById('show');
  appElement.innerHTML = selectedItemString;
};

const inSubmit = ref(false)

const selectedItemId = ref(null);
const selectedItemName = ref(null);
const selectedItemAge = ref(null);
const selectedItemAddress = ref(null);
const selectedItemStatus = ref(null);
const handleEditClick = (id,name,age,address,status) => {
  inSubmit.value = true
  selectedItemId.value = id;
  selectedItemName.value = name;
  selectedItemAge.value = age;
  selectedItemAddress.value = address;
  selectedItemStatus.value = status;
};
const handleSubmit = () => {
  document.getElementById('submit').innerHTML='Form submitted!'
  inSubmit.value = false

  const selectedItemIndex = action.findIndex(item => item.id === selectedItemId.value);
  if (selectedItemIndex !== -1) {
    action[selectedItemIndex].name = selectedItemName.value;
    action[selectedItemIndex].age = selectedItemAge.value;
    action[selectedItemIndex].address = selectedItemAddress.value;
    action[selectedItemIndex].status = selectedItemStatus.value;

    selectedItemId.value = null;
    selectedItemName.value = null;
    selectedItemAge.value = null;
    selectedItemAddress.value = null;
    selectedItemStatus.value = null;
  } else {
    console.error("Selected item not found in the action array!");
  }
};
</script>

<style scoped>
.brd{
  border: 1px solid black;
}
td,th{
  border: 1px solid black;
}
.text{
  text-align: center;
}
.text-status b{
  text-align: center;
  background-color: #6b5151;
}
.m-5{
  margin: 0 auto;
  padding: 20px;
}
.btn{
  border: none;
  background-color: white;
  cursor: pointer;
}
#submit{
  background-color: seagreen;
}
</style>