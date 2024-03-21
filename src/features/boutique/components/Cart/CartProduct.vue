<script setup lang="ts">
import type { ProductCartInterface } from "@/shared/interfaces";

defineProps<{
  product: ProductCartInterface;
}>();

const emit = defineEmits<{
  (e: "removeProductFromCart", productId: string): void;
}>();
</script>

<template>
  <div class="mb-10 p-10 d-flex flex-row align-items-center product">
    <strong class="mr-10">{{ product.title }}</strong>
    <span class="flex-fill mr-10">x {{ product.quantity }}</span>
    <span class="mr-10">Prix : {{ product.price }}€</span>
    <button
      class="btn btn-danger"
      @click="emit('removeProductFromCart', product._id)"
    >
      supprimer
    </button>
  </div>
</template>

<style lang="scss" scoped>
@use '@/assets/scss/mixins' as m;

.product {
  border: var(--border);
  border-radius: var(--border-radius);
  background-color: var(--gray-1);
  min-width: 100%;
  @include m.sm {
    width: 400px;
  }
  strong {
    font-size: 12px;
    @include m.sm {
      font-size: 15px;
    }
  }
  span {
    font-size: 12px;
    @include m.sm {
      font-size: 15px;
    }
  }
  button {
    padding: 6px;
    @include m.sm {
      padding: 8px 10px;
    }
  }
}
</style>
