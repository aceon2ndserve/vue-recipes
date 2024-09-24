<template>
<div class="max-w-[800px] mx-auto">
    <h1 class="text-5xl font-bold mb-5">{{ meal.strMeal }}</h1>
    <img :src='meal.strMealThumb' :alt="meal.strMeal">
    <div class="grid grid-cols-1 md:grid-cols-3 text-lg py-2">
        <div>
            <strong class="font-bold">Category:</strong> {{ meal.strCategory }}
        </div>
        <div>
           <strong class="font-bold" > Area:</strong> {{ meal.strArea }}
        </div>
        <div>
           <strong class="font-bold"> Tags:</strong> {{ meal.strTags }}
        </div>
    </div>
<div class="mb-2">
{{meal.strInstructions}}    
</div>
    <div class="grid grid-cols-1 md:grid-cols-2">
        <div >
            <h2 class="text-2xl font-semibold mb-3">Ingredients</h2>
            <template v-for="(el, i) of new Array(20)">
                
           <li class="list-none" v-if="meal[`strIngredient${i+1}`]">{{i+1}}. {{ meal[`strIngredient${i+1}`] }}</li>
            </template>
        </div>
        <div >
            <h2 class="text-2xl font-semibold mb-3">Measures</h2>
            <template v-for="(el, i) of new Array(20)">
                
                <li class="list-none" v-if="meal[`strMeasure${i+1}`]">{{i+1}}. {{ meal[`strMeasure${i+1}`] }}</li>
                 </template>
        </div>
        <div class="mt-2">
            <YoutubeButton :href="meal.strYoutube">Youtube</YoutubeButton>
        </div>
    </div>
</div>
</template>

<script setup>

import {ref, onMounted} from "vue"
import {useRoute} from "vue-router"
import axiosClient from "../axiosClient";
import YoutubeButton from "../components/YoutubeButton.vue";
const meal = ref({})
const route = useRoute()
onMounted(async ()=> {
    console.log(route.params.id)
    const {data} = await axiosClient.get(`lookup.php?i=${route.params.id}`)
   meal.value = data.meals[0] || {}
})
</script>