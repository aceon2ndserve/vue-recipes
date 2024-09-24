<template>
  <Meals :meals="meals" />

</template>

<script setup>
import {onMounted, ref} from "vue"
import axiosClient from "../axiosClient";
import Meals from "../components/Meals.vue";
const meals = ref([])
onMounted(async ()=> {
    for (let i = 0; i < 10; i++) {

        const {data} = await axiosClient.get('random.php')
       meals.value.push(data.meals[0])
    }
})
</script>
