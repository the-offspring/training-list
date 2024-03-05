<template>
	<div class="card">
		<div v-if="!card.unavailable">
			<div class="card-header">
				<h3 class="card-title">{{ card.title }}</h3>
				<!-- <button class="card_button"> <img src="@/assets/icon/edit_icon.svg"> </button> -->
			</div>
			<div class="card-body">
				<p class="card-text">{{ card.description }}</p>
				<div class="card-footer">
					<sapan>{{ card.duration }}</sapan>
				</div>

			</div> 
		</div>
	
		<p class="card__unavailable" v-else>Кажется, курс уже не существует...</p>

	</div>
</template>

<script setup>
const { card, index } = defineProps({
	index: { type: Number, },
	card: { type: Object, }
});



</script>

<style scoped>
img {
	width: 20px;
}

span {
	width: 100%;
}
.card {
	width: 100%;
	.card__unavailable {
		display: flex;
		
		margin: 0;
		padding-block: 5%;
		font-size: 20px;
		font-weight: 400;
		color: #fcb5ba;
		justify-content: center;
		align-items: center;
	}
}

.card-header {
	display: flex;
	justify-content: space-between;
}

.card_button {
	border: none;
	background-color: transparent;
}
</style>