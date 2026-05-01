<script setup>
import { ref, onMounted } from 'vue';
import ThemeToggler from './components/ThemeToggler.vue';
import AppHeader from './components/AppHeader.vue';
import LoadingState from './components/LoadingState.vue';
import ErrorState from './components/ErrorState.vue';
import RecipeCard from './components/RecipeCard.vue';

const recipe = ref(null);
const loading = ref(false);
const error = ref(null);
const isDark = ref(false);

const toggleTheme = () => {
  isDark.value = !isDark.value;
  document.documentElement.setAttribute('data-theme', isDark.value ? 'dark' : 'light');
};

const fetchRecipe = async () => {
  loading.value = true;
  error.value = null;
  recipe.value = null;
  
  try {
    const response = await fetch('https://www.themealdb.com/api/json/v1/1/random.php');
    if (!response.ok) throw new Error('Failed to fetch recipe');
    
    const data = await response.json();
    const meal = data.meals[0];
    
    // Process ingredients and measures
    const ingredients = [];
    for (let i = 1; i <= 20; i++) {
      const ingredient = meal[`strIngredient${i}`];
      const measure = meal[`strMeasure${i}`];
      
      if (ingredient && ingredient.trim() !== '') {
        ingredients.push(`${measure} ${ingredient}`);
      }
    }
    
    recipe.value = {
      id: meal.idMeal,
      title: meal.strMeal,
      category: meal.strCategory,
      area: meal.strArea,
      instructions: meal.strInstructions,
      thumbnail: meal.strMealThumb,
      youtube: meal.strYoutube,
      ingredients
    };
  } catch (err) {
    error.value = err.message;
  } finally {
    loading.value = false;
  }
};

onMounted(() => {
  fetchRecipe();
});
</script>

<template>
  <div class="container">
    <ThemeToggler :is-dark="isDark" @toggle="toggleTheme" />
    
    <AppHeader :loading="loading" @fetch="fetchRecipe" />

    <LoadingState v-if="loading" />

    <ErrorState v-else-if="error" :error="error" @retry="fetchRecipe" />

    <RecipeCard v-else-if="recipe" :recipe="recipe" />
  </div>
</template>
