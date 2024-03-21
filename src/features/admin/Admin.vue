<script setup lang="ts">
import AdminNav from "./components/AdminNav.vue";
</script>

<template>
  <div class="admin-container">
    <AdminNav
        class="admin-nav"
    />
    <div class="admin-main d-flex flex-fill justify-content-center align-items-center">
      <router-view v-slot="{ Component, route }">
        <Component :is="Component" :key="route.fullPath" />
      </router-view>
    </div>
  </div>
</template>

<style scoped lang="scss">
@use '@/assets/scss/mixins' as m;

.admin-container {
  width: 100%;
  display: initial;
  @include m.sm {
    height: 100%;
    width: 100%;
    display: flex;
    flex-direction: row;
  }
  .admin-main {
    margin: 20px 10px 20px 10px;
    @include m.sm {
      margin: 40px 20px 40px 20px;
    }
  }
}

.cont {
  overflow-y: auto;
  height: calc(100vh - 120px);
}
</style>
