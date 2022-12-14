<template>
  <div :class="highlightState ? 'table-row-highlight' : 'table-row'">
    <vue-avatar :size="30" color="#fff" :background-color="color" class="avatar">{{props.name[0]}}</vue-avatar>
    <span class="contact">{{ props.name }}</span>
    <span class="email">{{ props.email }}</span>
    <span class="phone">{{ props.phone }}</span>
    <div class="container-btns-options">
      <img @click="openModalEdit()" src="../assets/svgs/ic-edit.svg" class="ic_edit" />
      <img
        @click="openModalDel()"
        src="../assets/svgs/ic-delete.svg"
        class="ic_delete"
      />
    </div>
  </div>
</template>

<script setup>
import { defineProps, defineEmits, ref, onMounted } from "vue";
import VueAvatar from "@webzlodimir/vue-avatar";
import "@webzlodimir/vue-avatar/dist/style.css";

const color = ref('');
const highlightState = ref(true);

const props = defineProps(["id", "name", "email", "phone"]);

const emit = defineEmits(["openDeleteModal", "openEditModal"]);

function openModalDel() {
  emit("openDeleteModal", props.id);
}

function openModalEdit() {
  emit("openEditModal", {id: props.id, name: props.name, email:props.email, phone: props.phone});
}

function generateColor() {
  const letters = '0123456789ABCDEF';
  let colorBg = '#';
  
  for (let i = 0; i < 6; i++) {
    colorBg += letters[Math.floor(Math.random() * 16)];
  }
  
  color.value = colorBg; 
}

function highlight(){
  setTimeout(() => {
    highlightState.value = false;
  }, 10000)
}

onMounted(() => (
  generateColor(),
  highlight()
))

</script>

<style scoped>
.table-row {
  cursor: pointer;
  display: flex;
  flex-direction: row;
  align-items: center;
  width: 98vw;
  height: 3.2rem;
  border-radius: 4px;
  border: solid 1px #e1e1e1;
  background-color: #ffffff;
}

.table-row-highlight {
  cursor: pointer;
  display: flex;
  flex-direction: row;
  align-items: center;
  width: 98vw;
  height: 3.2rem;
  border-radius: 4px;
  border: solid 1px #e1e1e1;
  background-color: #fff3f2;
}

.table-row:hover {
  background-color: #fff3f2;
}

.contact {
  width: 3.313rem;
  height: 0.938rem;
  margin-left: 1%;
  font-size: 1rem;
  color: #000000;
  white-space: nowrap;
}

.email {
  width: 2.25rem;
  height: 0.938rem;
  margin-left: 24%;
  font-size: 1rem;
  color: #000000;
  white-space: nowrap;
}

.phone {
  width: 3.188rem;
  height: 0.938rem;
  margin-left: 29%;
  font-size: 1rem;
  color: #000000;
  white-space: nowrap;
}

.container-btns-options {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  margin-left: 32%;
  width: 60px;
}

img.ic_edit {
  width: 1rem;
  height: 1rem;
  object-fit: contain;
}

img.ic_delete {
  align-self: flex-end;
  width: 1rem;
  height: 1rem;
  object-fit: contain;
}

.avatar {
  margin-left: 0.5%;
}
</style>