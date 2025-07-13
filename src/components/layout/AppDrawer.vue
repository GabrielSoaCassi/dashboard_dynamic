<template>
   <nav :class="['drawer', { open: open }]">
    <div class="drawer-header">
      <span style="color:aquamarine;display:flex;align-items:center;gap:8px;">
        Dynamic Dashboard
      </span>
      <button @click="emit('close')" class="close-btn">
        <X size="28" />
      </button>
    </div>
    <ul>
    </ul>
  </nav>
</template>

<script setup>
import {X} from 'lucide-vue-next'
    const props = defineProps({
        open: {
            type: Boolean,
            default: false
        }
    });
    const emit = defineEmits(['close']);
</script>

<style scoped type="text/scss">
.drawer {
    position: fixed;
    top: 0;
    left: 0;
    bottom: 0;
    width: 368px;
    background: #242424;
    box-shadow: 2px 0 16px rgba(0, 0, 0, 0.08);
    transform: translateX(-100%);
    transition: transform 0.3s;
    z-index: 100;
    display: flex;
    flex-direction: column;
}

.drawer.open {
    transform: translateX(0);
}

.drawer-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 20px 16px 8px 16px;
}

.close-btn {
    background: none;
    color: aquamarine;
    border: none;
    font-size: 2rem;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
}


</style>