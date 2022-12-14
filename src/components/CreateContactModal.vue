<template>
  <div class="bg-modal">
    <div class="modal-wrapper">
      <span class="create-new-contact">Criar novo contato</span>
      <div class="divisor"></div>
      <label for="name">Nome</label>
      <input
        v-model="name"
        class="text-field"
        id="name"
        type="text"
        autofocus
      />
      <label for="email">E-mail</label>
      <input v-model="email" class="text-field" id="email" type="text" />
      <label for="phone">Telefone</label>
      <input v-model="phone" class="text-field-phone" id="phone" type="text" />
      <div class="divisor"></div>
      <div class="container-btns">
        <span @click="closeModal()" class="cancel">Cancelar</span>
        <button
          :disabled="name === '' && email === '' && phone === ''"
          @click="saveData()"
          :class="name === '' && email === '' && phone === '' ? 'btn-save-disable' : 'btn-save'"
        >
          <span class="txt-save">Salvar</span>
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { defineEmits, ref } from "vue";

let name = ref("");
let email = ref("");
let phone = ref("");

const emit = defineEmits(["closeModalCreate", "save"]);

function closeModal() {
  emit("closeModalCreate");
}

function saveData() {
  emit("save", { name: name.value, email: email.value, phone: phone.value });
  name.value = "";
  email.value = "";
  phone.value = "";
  emit("closeModalCreate");
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

.create-new-contact {
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
  background-color: #ffffff;
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
  font-size: 0.875rem;
  font-weight: 600;
  text-align: center;
  color: #fa7268;
}

.btn-save {
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

.btn-save-disable {
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

.txt-save {
  width: 2.5rem;
  height: 1rem;
  font-family: Roboto;
  font-size: 0.875rem;
  font-weight: 600;
  text-align: center;
  color: #ffffff;
}
</style>