<script setup>
defineProps({
  error: String
});

defineEmits(['retry']);
</script>

<template>
  <div class="error" style="text-align: center; color: #e74c3c;">
    <p>{{ error }}</p>
    <button @click="$emit('retry')" style="margin-top: 10px;">Try Again</button>
  </div>
</template>
