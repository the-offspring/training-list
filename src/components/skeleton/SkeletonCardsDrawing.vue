<template>
    <div class="training-list">
        <addSkeletonCard
            v-for="(card, index) in cardsCopy" 
            :key="card.id" 
            :card="card" 
            :index="index"
        />
    </div>
</template>

<script setup>
import addSkeletonCard from '@/components/skeleton/SkeltonCardCreat.vue'

const props = defineProps({
cardsCopy: {
    type: Array,
}
});

</script>

<style scoped>
@import '/src/assets/global.css';

</style>
