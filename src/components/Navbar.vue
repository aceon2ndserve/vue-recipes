<template>
    <header class="bg-white shadow h-16 justify-between flex items-strech">
    <router-link :to="{name: 'home'}" class="inline-flex items-center h-full px-5">
Home
    </router-link>
    <div class="flex items-center gap-1">
        <router-link :to="{name: 'byName'}" class="inline-flex items-center px-2 h-full hover:bg-purple-200 transition">
            Search Meals
        </router-link>
        <router-link :to="{name: 'byLetter'}" class="inline-flex items-center px-2 h-full hover:bg-purple-200 transition">
            Meals by Letter
        </router-link>
        <router-link :to="{name: 'ingredients'}" class="inline-flex items-center px-2 h-full hover:bg-purple-200 transition">
            Meals by Ingredients
        </router-link>
    </div>
</header>
</template>