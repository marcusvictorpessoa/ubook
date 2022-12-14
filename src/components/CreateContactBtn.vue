<template>
  <div class="container-btn">
    <img src="../assets/svgs/ic-plus.svg" class="ic_plus" />
    <span class="Criar-contato Text-Style-3">Criar contato</span>
  </div>
</template>

<script setup>
</script>

<style scoped >
.container-btn {
  cursor: pointer;
  display: flex;
  align-items: center;
  width: 9rem;
  height: 2.5rem;
  padding: 0.5rem 1.3rem;
  border-radius: 20px;
  box-shadow: inset 0 0 0 1px rgba(255, 255, 255, 0.16),
    0 0 0 0.5px rgba(0, 0, 0, 0.08), inset 0 0 0 0.5px rgba(0, 0, 0, 0.08),
    0 2px 4px 0.5px rgba(0, 0, 0, 0.16);
  background-color: #dbff90;
}

.container-btn:hover {
  box-shadow: 1px 1px 1px #888;
}

.Criar-contato {
  width: 5.125rem;
  height: 1rem;
  margin: 0 0 0 0.5rem;
  font-size: 0.875rem;
  font-weight: 600;
  white-space: nowrap;
  color: #fa7268;
}

img.ic_plus {
  width: 1rem;
  height: 1rem;
  object-fit: contain;
}
</style>