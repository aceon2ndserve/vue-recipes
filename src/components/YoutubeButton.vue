<template>
     <div>
                <a :href="href" target="_blank" class="px-3 py-2 rounded border bg-red-500 border-red-600 hover:text-white transition"><slot></slot></a>
            </div>
</template>

<script setup>
const props = defineProps({
    href: String
})
</script>