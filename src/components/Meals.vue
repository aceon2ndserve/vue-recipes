<template>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-5 p-8">
       <MealItem v-for="meal of meals" :key="meal.idMeal" :meal="meal"/>
    </div>
    <div class="flex justify-center" v-if="!meals.length">
        No Meals found...
    </div>
</template>
<script setup>

import MealItem from './MealItem.vue';
const {meals} = defineProps({
    meals: {
        required:true,
        type: Array
    }
})
</script>