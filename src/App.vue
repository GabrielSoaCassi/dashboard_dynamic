<template>
  <div class="app-container">
    <header class="topbar">
      <button class="menu-btn" @click="open = true">
        <Menu size="28" />
      </button>
      <app-drawer :open="open" @close="open = false"></app-drawer>
    </header>
    <main class="main-content">
      <router-view />
    </main>
  </div>
</template>

<script setup>
import AppDrawer from './components/layout/AppDrawer.vue'
import { Menu } from 'lucide-vue-next'
import { ref } from 'vue';

const open = ref(false)
</script>

<style scoped>
.topbar {
  align-items: center;
  gap: 12px;
  padding: 16px;
  width: 100vw;
  position: sticky;
  top: 0;
  z-index: 10;
}

.menu-btn {
  font-size: 1.8rem;
  background: none;
  border: none;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
}

.app-container {
  display: flex;
  flex-direction: column;
  height: 100vh;
}
.main-content {
  flex: 1;
  padding: 16px;
  width: 100vw;
  overflow-y: auto;
}
</style>
