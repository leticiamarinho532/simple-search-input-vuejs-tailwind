<script lang="ts">
import ListItems from '../list-items/ListItems.vue'
import { MagnifyingGlassIcon } from '@heroicons/vue/24/solid'

export default {
    components: {
        ListItems,
        MagnifyingGlassIcon
    }
}
</script>

<template>
    <div class="max-w-md">
        <div class="relative border border-slate-200 rounded-md">
            <input class="w-5/6 focus:outline-none" type="text" placeholder="Selecione o país">
            <MagnifyingGlassIcon 
                class="pointer-events-none h-5 w-5 text-slate-700 absolute top-1/2 transform -translate-y-1/2 right-4"
            />
        </div>
        <ListItems />
    </div>
</template>

<style scoped>
</style>