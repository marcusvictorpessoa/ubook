<template>
  <div class="table-header">
      <span class="contact">Contatos</span>
      <span class="email">E-mail</span>
      <span class="phone">Telefone</span>
    </div>
</template>

<script setup>
</script>

<style scoped>
.table-header {
  display: flex;
  flex-direction: row;
  align-items: center;
  width: 98vw;
  height: 3.2rem;
  border-radius: 4px;
  border: solid 1px #e1e1e1;
  background-color: #ffffff;
}

.contact {
  width: 3.313rem;
  height: 0.938rem;
  margin-left: 3%;
  font-size: 1rem;
  color: #9198af;
  white-space: nowrap;
}

.email {
  width: 2.25rem;
  height: 0.938rem;
  margin-left: 24%;
  font-size: 1rem;
  color: #9198af;
  white-space: nowrap;
}

.phone {
  width: 3.188rem;
  height: 0.938rem;
  margin-left: 29%;
  font-size: 1rem;
  color: #9198af;
  white-space: nowrap;
}
</style>