<template>
  <div class="bg-modal">
    <div class="modal-wrapper">
      <span class="edit-contact">Editar contato</span>
      <div class="divisor"></div>
      <label for="name">Nome</label>
      <input
        v-model="nameInput"
        class="text-field"
        id="name"
        type="text"
      />
      <label for="email">E-mail</label>
      <input
        v-model="emailInput"
        class="text-field"
        id="email"
        type="text"
      />
      <label for="phone">Telefone</label>
      <input
        v-model="phoneInput"
        class="text-field-phone"
        id="phone"
        type="text"
      />
      <div class="divisor"></div>
      <div class="container-btns">
        <span @click="closeModal()" class="cancel">Cancelar</span>
        <button
          :disabled="nameInput === '' && emailInput === '' && phoneInput === ''"
          @click="editData()"
          :class="nameInput === '' && emailInput === '' && phoneInput === '' ? 'btn-edit-disable' : 'btn-edit'"
        >
          <span class="txt-edit">Salvar</span>
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { defineEmits, ref, defineProps, onMounted } from "vue";

const props = defineProps(["id", "name", "email", "phone"]);

let nameInput = ref("");
let emailInput = ref("");
let phoneInput = ref("");

onMounted(() => {
  nameInput.value = props.name;
  emailInput.value = props.email;
  phoneInput.value = props.phone;
})

const emit = defineEmits(["closeModalEdit", "edit"]);

function closeModal() {
  emit("closeModalEdit");
}

function editData() {
  emit("edit", {
    idEdit: props.id,
    nameEdit: nameInput.value,
    emailEdit: emailInput.value,
    phoneEdit: phoneInput.value,
  });
  emit("closeModalEdit");
}
</script>

<style scoped>
.bg-modal {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  position: absolute;
  z-index: 5;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.4);
}

.modal-wrapper {
  width: 29rem;
  height: 22rem;
  padding: 1rem 0;
  border-radius: 16px;
  box-shadow: 0 16px 10px 0 rgba(0, 0, 0, 0.16);
  background-color: #ffffff;
}

.edit-contact {
  cursor: default;
  width: 8.25rem;
  height: 1.188rem;
  margin: 0 7.75rem 0.781rem 1rem;
  font-family: Roboto;
  font-size: 1rem;
  font-weight: normal;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: normal;
  color: #000000;
}

.divisor {
  width: 100%;
  height: 0.125rem;
  margin: 0.781rem 0 1.219rem;
  border: solid 1px #c0c3d2;
}

label {
  width: 2.375rem;
  height: 1rem;
  margin: 1.219rem 13.125rem 0.25rem 1.5rem;
  font-family: Roboto;
  font-size: 0.875rem;
  font-weight: normal;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: normal;
  color: #000000;
}

.text-field-phone {
  width: 8rem;
  height: 2rem;
  margin: 0.25rem 7.5rem 0.5rem 1.5rem;
  padding: 0.5rem 0.875rem 0.5rem 0.625rem;
  border-radius: 4px;
  border: solid 1px #c0c3d2;
  background-color: var(--white-two);
}

.text-field {
  width: 26rem;
  height: 2rem;
  padding-left: 0.875rem;
  margin: 0.25rem 1.5rem 1rem;
  border-radius: 4px;
  border: solid 1px #c0c3d2;
  background-color: #ffffff;
}

.container-btns {
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: flex-end;
  align-items: center;
}

.cancel {
  cursor: pointer;
  width: 3.5rem;
  height: 1rem;
  margin-right: 1rem;
  font-family: Roboto;
  font-size: 0.875rem;
  font-weight: 500;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: normal;
  text-align: center;
  color: #fa7268;
}

.btn-edit {
  cursor: pointer;
  width: 4.5rem;
  height: 2rem;
  padding: 0.5rem 1rem;
  margin-right: 1.5rem;
  border-radius: 16px;
  box-shadow: inset 0 0 0 1px rgba(255, 255, 255, 0.16),
    0 0 0 0.5px rgba(0, 0, 0, 0.08), inset 0 0 0 0.5px rgba(0, 0, 0, 0.08),
    0 2px 4px 0.5px rgba(0, 0, 0, 0.16);
  background-color: #fa7268;
  border: none;
}

.btn-edit-disable {
  cursor: pointer;
  width: 4.5rem;
  height: 2rem;
  padding: 0.5rem 1rem;
  margin-right: 1.5rem;
  border-radius: 16px;
  box-shadow: inset 0 0 0 1px rgba(255, 255, 255, 0.16),
    0 0 0 0.5px rgba(0, 0, 0, 0.08), inset 0 0 0 0.5px rgba(0, 0, 0, 0.08),
    0 2px 4px 0.5px rgba(0, 0, 0, 0.16);
  background-color: #fa7268;
  border: none;
  opacity: 0.32;
}

.txt-edit {
  width: 2.5rem;
  height: 1rem;
  font-family: Roboto;
  font-size: 0.875rem;
  font-weight: 500;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: normal;
  text-align: center;
  color: #ffffff;
}
</style>