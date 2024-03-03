<template>
	<div class="card"> 
		<div v-if="!card.unavailable">
			<h3 class="card__title">{{ card.title }}</h3>
			<p class="card__description">{{ card.description }}</p>
			<span class="card__duration">{{ card.duration }}</span>
		</div>
			<p class="card__unavailable" v-else>Кажется, курс уже не существует...</p>
	</div>
</template>

<script setup>
const { card, index} = defineProps({
	index: { type: Number, },
	card: { type: Object, }
});
</script>

<style scoped>

.card {
	width: 93%;
	min-height: 111px;
	display: inline-block;
	padding: 10px 20px;
	background-color: #f5f5f5;
	border-radius: 16px;
}

.card__title {
	margin: 0;
	padding: 0;
	font-size: 20px;
	font-weight: 600;
	margin-bottom: 8px;
}

.card__description {
	margin: 0;
	padding: 0;
	color: rgb(106, 109, 114);
	margin-bottom: 16px;
}

.card__duration {
	margin: 0;
	font-size: 12px;
	font-weight: 600;
}

.card__unavailable {
	margin: 0;
	font-size: 20px;
	font-weight: 400;
	text-align: center;
	color: #fcb5ba;
}
</style>