<script lang="ts">
import ListItems from '../list-items/ListItems.vue'
import { MagnifyingGlassIcon } from '@heroicons/vue/24/solid'

declare interface Items {
    text: string
}

export default {
    components: {
        ListItems,
        MagnifyingGlassIcon
    },
    data () {
        return {
            filter: '',
            items: [] as Items[]
        }
    },
    created() {
        var i = 0;

        for (; i < 200; i++) {
            var randomText: string = Math.random().toString(36)
            this.items.push({
                text: randomText
            })
        }
    },
    computed:{
        itemsWithFilter() {
            if (this.filter) {
                let regularExpression = new RegExp(this.filter.trim(), 'i')

                return this.items.filter(item => regularExpression.test(item.text))
            }

            return this.items
        }
    }
}
</script>

<template>
    <div class="max-w-md">
        <div class="relative border border-slate-200 rounded-md">
            <input class="w-5/6 focus:outline-none" v-on:input="filter = $event.target.value" type="text" placeholder="Selecione o item">
            <MagnifyingGlassIcon 
                class="pointer-events-none h-5 w-5 text-slate-700 absolute top-1/2 transform -translate-y-1/2 right-4"
            />
        </div>
        <div class="grid grid-cols-3 gap-2">
            <div 
                class="list-none rounded-md hover:bg-gray-100 text-center"
                v-for="item of itemsWithFilter"
            >
                <ListItems :text="item.text"/>
            </div>
        </div>
    </div>
</template>

<style scoped>
</style>