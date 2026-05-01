<script setup>
defineProps({
  loading: Boolean
});

defineEmits(['fetch']);
</script>

<template>
  <header style="text-align: center; margin-bottom: 40px;">
    <h1 style="font-size: 2.5rem; margin-bottom: 10px;">Random Recipe Generator</h1>
    <p style="color: var(--text-light); margin-bottom: 20px;">Hungry? Let us decide what you'll cook today!</p>
    <button @click="$emit('fetch')" class="btn-primary" :disabled="loading">
      {{ loading ? 'Finding something tasty...' : 'Get Random Recipe' }}
    </button>
  </header>
</template>
