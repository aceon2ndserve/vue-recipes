<template>
  <div class="flex flex-col p-8 justify-center items-center gap-2 mt-2">

<div class="flex gap-3 mt-2">
<router-link :to="{name: 'byLetter', params: {letter}}" v-for="letter of letters.split('')" :key="letter">
{{letter}}
</router-link>
</div>
<Meals :meals="meals"/>
</div>
</template>

<script setup>
import {onMounted, watch} from "vue"
import {computed} from "@vue/reactivity"
import {useRoute} from "vue-router"
import store from "../store";
import MealItem from "../components/MealItem.vue";
import Meals from "../components/Meals.vue";
const route = useRoute()
const letters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
const meals = computed(()=> store.state.mealsByLetter )
onMounted(()=> {
    store.dispatch('searchMealsByLetter', route.params.letter)
})

watch(route, ()=> store.dispatch('searchMealsByLetter', route.params.letter))
</script>

