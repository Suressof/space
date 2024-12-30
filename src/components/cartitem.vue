<script setup>
import card from './card.vue';
import app from '@/App.vue'
defineProps ({
    items: Array
})
</script>


<template>
     <!-- <div class="border border-slate-100 p-4 rounded-xl">
        <img src="/src/assets/1.png">

        <div class="flex justify-between">
            <p>NGHE45</p>

            <div class="flex justify-between mt-2">
                <b>1250 $</b>
                <img class="opacity-40 hover:opacity-100 cursor-pointer transition" src="/src/assets/close.svg">

            </div>
        </div>
    </div>-->
    <div class="grid grid-cols-4 gap-5">
        <card
        v-for="item in items" 
        :key="item.id"
        :name="item.name"
        :image="item.image"
        :price="item.price"
        />
        </div>
</template>