<template>
	<div class="training-list">
		<addCard
			v-for="(card, index) in cards" 
			:key="card.id" 
			:card="card" 
			:index="index"
			@click="emit('click-by-card', card)" 
		/>
	</div>
</template>

<script setup>
import addCard from './CardCreat.vue'

const props = defineProps({
	cards: {
		type: Array,
	}
});

const emit = defineEmits(['click-by-card']);
</script>

