<template>
  <app-header
    :btnCreateIsActive="contacts.length !== 0"
    @openCreateModal="showCreateModal()"
  />
  <div v-show="contacts.length === 0" class="content-none-data">
    <img src="./assets/svgs/ic-book.svg" class="ic-book" />
    <span class="none-contact"> Nenhum contato foi criado ainda.</span>
    <create-contact-btn @click="showCreateModal()" />
  </div>
  <create-contact-modal
    @save="saveContact($event)"
    @closeModalCreate="hiddenCreateModal()"
    v-show="createModal"
  />
  <edit-contact-modal
    v-if="editModal"
    @edit="editContact($event)"
    @closeModalEdit="hiddenEditModal()"
    :id="rowEdit.id"
    :name="rowEdit.name"
    :email="rowEdit.email"
    :phone="rowEdit.phone"
  />
  <delete-contact-modal
    v-show="deleteModal"
    @deleteRowSelected="deleteRow()"
    @closeModalDelete="hiddenDeleteModal()"
  />
  <div v-show="contacts.length !== 0" class="content-data">
    <table-header />
    <div v-for="contact in contacts" :key="contact.id">
      <table-row
        :id="contact.id"
        :name="contact.name"
        :email="contact.email"
        :phone="contact.phone"
        @openDeleteModal="showDeleteModal($event)"
        @openEditModal="showEditModal($event)"
      />
    </div>
  </div>
</template>

<script setup>
import { ref, reactive } from "vue";
import CreateContactBtn from "./components/CreateContactBtn.vue";
import CreateContactModal from "./components/CreateContactModal.vue";
import EditContactModal from "./components/EditContactModal.vue";
import DeleteContactModal from "./components/DeleteContactModal.vue";
import AppHeader from "./components/AppHeader.vue";
import TableHeader from "./components/TableHeader.vue";
import TableRow from "./components/TableRow.vue";

let createModal = ref(false);
let editModal = ref(false);
let deleteModal = ref(false);

let idRowToDel = ref("");
let rowEdit = ref({ id: "", name: "", email: "", phone: "" });

let contacts = reactive([]);

function showCreateModal() {
  createModal.value = true;
}

function hiddenCreateModal() {
  createModal.value = false;
}

function saveContact(e) {
  contacts.push(
    Object.assign(e, { id: Math.floor(Date.now() * Math.random()).toString(8) })
  );
}

function showEditModal(e) {
  editModal.value = true;
  rowEdit.value = e;
}

function hiddenEditModal() {
  editModal.value = false;
}

function editContact(e) {
  contacts = contacts.filter((el) => {
    if (el.id === e.idEdit) {
      el.name = e.nameEdit;
      el.email = e.emailEdit;
      el.phone = e.phoneEdit;
      return el;
    } else {
      return el;
    }
  });
  rowEdit.value = { id: "", name: "", email: "", phone: "" };
}

function showDeleteModal(e) {
  deleteModal.value = true;
  idRowToDel.value = e;
}

function hiddenDeleteModal() {
  deleteModal.value = false;
}

function deleteRow() {
  contacts = contacts.filter((el) => {
    if (el.id !== idRowToDel.value) {
      return el;
    }
  });
  idRowToDel.value = "";
  deleteModal.value = false;
}
</script>

<style>
@import "../node_modules/@fontsource/roboto/index.css";

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: Roboto;
}

body {
  background-color: #f8f9fd;
  overflow-y: auto;
}

.content-none-data {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.content-data {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
  margin-top: 1.5rem;
}

.ic-book {
  width: 14.813rem;
  height: 12.5rem;
  margin-top: 7rem;
  object-fit: contain;
}

.none-contact {
  cursor: default;
  width: 14.875rem;
  height: 1.188rem;
  margin: 1.5rem 0;
  font-family: Roboto;
  font-size: 1rem;
  font-weight: normal;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: normal;
  text-align: center;
  color: #000000;
}
</style>
