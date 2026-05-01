<script setup>
defineProps({
  recipe: {
    type: Object,
    required: true
  }
});
</script>

<template>
  <div class="recipe-card">
    <div class="recipe-header">
      <img :src="recipe.thumbnail" :alt="recipe.title" class="recipe-img">
    </div>
    
    <div class="recipe-content">
      <h2 style="font-size: 2rem; margin-bottom: 10px;">{{ recipe.title }}</h2>
      
      <div class="recipe-info">
        <span class="badge">{{ recipe.category }}</span>
        <span class="badge">{{ recipe.area }}</span>
      </div>

      <div style="margin-top: 30px;">
        <h3>Ingredients</h3>
        <ul class="ingredients-list">
          <li v-for="(ing, index) in recipe.ingredients" :key="index">
            {{ ing }}
          </li>
        </ul>
      </div>

      <div style="margin-top: 30px;">
        <h3>Instructions</h3>
        <p class="instructions">{{ recipe.instructions }}</p>
      </div>

      <a v-if="recipe.youtube" :href="recipe.youtube" target="_blank" class="youtube-link">
        📺 Watch on YouTube
      </a>
    </div>
  </div>
</template>
