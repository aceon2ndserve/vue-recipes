<template>
    <div class="p-8">
        <h1 class="text-4xl font-bold mb-4">Ingredients</h1>
        <div class="p-8">
            <input type="text" v-model="keyword" class="rounded border-2 border-gray-200 w-full" placeholder="Search for Ingredients">
        </div>
 <router-link :to="{name: 'byIngredient', params: {ingredient: ing.strIngredient}}" v-for="ing in computedIngredients" :key="ing.id" class="block bg-white shadow rounded p-3 mb-3">
    <h3 class="text-2xl mb-2 font-bold">{{ ing.strIngredient }}</h3>
    <p>{{ ing.strDescription }}</p>
</router-link>
</div>
</template>

<script setup>
import {onMounted, ref} from "vue"
import {computed} from "@vue/reactivity"
import axiosClient from "../axiosClient";

const keyword = ref("")

const ingredients = ref([])

const computedIngredients = computed(()=>{
    return ingredients.value.filter(i => i.strIngredient.toLowerCase().includes(keyword.value.toLowerCase()))
})
onMounted(() => {
    axiosClient.get('list.php?i=list').then(({data}) => {

     ingredients.value = data.meals
    }
)})
</script>

