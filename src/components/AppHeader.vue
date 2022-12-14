<template>
  <header>
    <img src="../assets/svgs/ic-logo.svg" alt="logo do Ubook" />
    <div>
      <create-contact-btn v-show="props.btnCreateIsActive" @click="openModal()" />
      <filter-input />
    </div>
  </header>
</template>

<script setup>
import CreateContactBtn from "./CreateContactBtn.vue";
import FilterInput from "./FilterInput.vue";

import { defineProps, defineEmits } from "vue";

const props = defineProps(['btnCreateIsActive'])

const emit = defineEmits(['openCreateModal']);

function openModal(){
  emit('openCreateModal');
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
header {
  background-color: #f8f9fd;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  width: 100vw;
  height: 4rem;
  padding: 1rem;
}

div {
  display: flex;
  flex-direction: row;
  align-items: center;
}
</style>
