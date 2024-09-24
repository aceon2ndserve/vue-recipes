<template>
    <div class="p-8 pb-0">
        <input v-model="keyword" @input="searchMeals" type="text" class="rounded border-2 border-gray-200 w-full" placeholder="Search for Meals">
    </div>
    <Meals :meals="meals"/>

</template>

<script setup>
import {ref, onMounted} from "vue"
import {computed} from "@vue/reactivity"
import {useRoute} from "vue-router"
import store from "../store";
import Meals from "../components/Meals.vue";
const keyword = ref("")
const route = useRoute()
onMounted(()=> {
    keyword.value = route.params.name
    if (keyword.value) {
        searchMeals()
}})
const meals = computed(()=> store.state.searchedMeals)
function searchMeals() {
    store.dispatch('searchMeals', keyword)

}
</script>

