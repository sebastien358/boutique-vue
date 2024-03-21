<script setup lang="ts">
import { useAdminProducts } from "../stores/adminProductStore";

const adminProductStore = useAdminProducts();
function tryDeleteProduct(productId: string) {
  adminProductStore.deleteProduct(productId);
}
</script>

<template>
  <div class="container card">
    <h3 v-if="adminProductStore.isLoading">Chargement ...</h3>
    <ul v-else>
      <li
        class="d-flex flex-row align-items-center"
        v-for="product of adminProductStore.products"
        :key="product._id"
      >
        <span class="flex-fill">{{ product.title }}</span>
        <router-link :to="{ name: 'edit', params: { productId: product._id } }">
          <button class="btn btn-primary mr-5">Modifier</button>
        </router-link>
        <button @click="tryDeleteProduct(product._id)" class="btn btn-danger">
          Supprimer
        </button>
      </li>
    </ul>
  </div>
</template>

<style scoped lang="scss">
@use '@/assets/scss/mixins' as m;

.card {
  padding: 0;
  width: 100%;
  overflow-y: auto;
  height: calc(100vh - 210px);
  @include m.sm {
    height: initial;
    width: 60%;
  }
}

li {
  border: var(--border);
  border-radius: var(--border-radius);
  padding: 15px 10px;
  margin-bottom: 5px;
  cursor: pointer;
  transition: all 0.2s;
  span {
    font-size: 13px;
    @include m.sm {
      font-size: 15px;
    }
  }
  button {
    padding: 6px;
    @include m.sm {
      padding: 8px;
    }

  }
  &:hover {
    background-color: var(--gray-1);
  }
}
</style>
