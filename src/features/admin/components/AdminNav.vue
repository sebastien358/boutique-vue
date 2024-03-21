<script setup lang="ts">
</script>

<template>
  <div class="admin-nav">
    <nav class="card d-flex flex-column">
      <h3 class="mb-20">Produits</h3>
      <router-link class="mb-10 link" to="/admin/productlist">Liste des produits</router-link>
      <router-link class="mb-10 link" to="/admin/addproduct">Ajouter un produit</router-link>
    </nav>
  </div>

</template>

<style scoped lang="scss">
@use '@/assets/scss/mixins' as m;

.admin-nav {
  padding: 0;
  //height: calc(100vh - 170px);
  height: 100vh;
  @include m.sm {
    height: initial;
  }
  h3 {
    text-align: center;
    font-size: 16px;
    @include m.sm {

      text-align: start;
    }
  }
}

.card {
  border: 0;
  border-radius: 0;
  background-color: rgba(0, 0, 0, 0.80);
  width: 100%;
  height: auto;
  color: white;
  padding: 15px 10px;
  top: 47px;
  @include m.sm {
    border: var(--border);
    border-radius: var(--border-radius);
    height: calc(100vh - 140px);
    color: black;
    background-color: white;
    width: 200px;
  }
  .link {
    white-space: nowrap;
    color: white;
    font-size: 11px;
    @include m.sm {
      color: black;
    }
  }
}
</style>
