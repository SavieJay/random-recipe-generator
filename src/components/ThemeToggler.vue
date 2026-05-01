<script setup>
defineProps({
  isDark: Boolean
});

defineEmits(['toggle']);
</script>

<template>
  <button 
    @click="$emit('toggle')" 
    class="theme-toggle" 
    :title="isDark ? 'Switch to Light Mode' : 'Switch to Dark Mode'"
  >
    {{ isDark ? '☀️' : '🌙' }}
  </button>
</template>
