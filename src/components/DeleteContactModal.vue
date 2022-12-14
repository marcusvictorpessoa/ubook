<template>
  <div class="bg-modal">
    <div class="modal-wrapper">
      <span class="edit-contact">Editar contato</span>
      <div class="divisorTop"></div>
      <span class="msg-delete"> Deseja realmente excluir o contato? </span>
      <div class="divisorBottom"></div>
      <div class="container-btns">
        <span @click="closeModalDel()" class="cancel">Cancelar</span>
        <div @click="delRow()" class="btn-delete">
          <span class="txt-delete">Excluir</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { defineEmits } from "vue";

const emit = defineEmits(["closeModalDelete", "deleteRowSelected"]);

function closeModalDel() {
  emit("closeModalDelete");
}

function delRow(){
  emit('deleteRowSelected');
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
  height: 13rem;
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

.divisorTop {
  width: 100%;
  height: 0.125rem;
  margin: 0.781rem 0 1.219rem;
  border: solid 1px #c0c3d2;
}

.divisorBottom {
  width: 100%;
  height: 0.125rem;
  margin: 3.5rem 0 1.219rem;
  border: solid 1px #c0c3d2;
}

.msg-delete {
  width: 13.875rem;
  height: 1rem;
  margin: 1.219rem 1.125rem 7.563rem 1.5rem;
  font-family: Roboto;
  font-size: 0.875rem;
  font-weight: normal;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: normal;
  color: #000000;
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

.btn-delete {
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
}

.txt-delete {
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