<template>
  <div class="search">
    <input placeholder="Buscar..." />
    <img src="../assets/svgs/ic-search.svg" class="fa fa-search" />
  </div>
</template>

<script setup>
</script>


<style>
.search {
  position: relative;
  display: flex;
  color: #e4e7f4;
  font-size: 16px;
  padding: 0.438rem 0.5rem 0.375rem;
}

.search input {
  display: flex;
  width: 70vw;
  height: 32px;
  height: 2rem;
  background: #e4e7f4;
  border: 1px solid #e4e7f4;
  border-radius: 4px;
}

.search input {
  text-indent: 10px;
}

.search .fa-search {
  position: absolute;
  top: 15px;
  right: 15px;
}
</style>