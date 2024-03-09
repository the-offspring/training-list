<template>
	<div class="container">
		<h1 class="title">Список курсов</h1>
		<CardsDrawing v-if="!cardsIsLoading" :cards="cards" @click-by-card="openCardForEdit" />
		<SkeletonCardsDrawing v-else :cardsCopy="cards !== null || undefined ? cardsCopy : cards"/>

		<EditModal class="modal-window" v-if="show.value === true" :card="defaultCardObject" @set-card="updatedCard" @save-card="saveCard" :show-modal="showModal"/>
	</div>
</template>

<script setup>
import EditModal from './components/modal/EditModal.vue';
import CardsDrawing from './components/CardsDrawing.vue';
import SkeletonCardsDrawing from './components/skeleton/SkeletonCardsDrawing.vue';
import { ref } from 'vue';

const cardForEdit = ref({
	id: 0,
	title: '',
	description: '',
	duration: '',
	unavailable: false,
})

var cardsIsLoading = ref( true );
var show = ref( false );

const cards = ref([]);

const cardsCopy = ref([
			{
				id: 1,
				title: '',
				description: '',
				duration: 10,
				unavailable: false,
			},
			{
				id: 2,
				title: '',
				description: '',
				duration: 6,
				unavailable: false,
			},
			{
				id: 3,
				title: '',
				description: '',
				duration: 7,
				unavailable: false,
			},
			{
				id: 4,
				title: '',
				description: '',
				duration: 7,
				unavailable: false,
			},
]);

const cardsLoading = () => {
	cardsIsLoading.value = true;
	setTimeout(() => {
		cards.value = [
			{
				id: 1,
				title: 'Python-разработчик',
				description: 'Описание: На Python пишут сайты, приложения, игры и чат-боты. Netflix, Spotify, Google, Dropbox и Youtube написаны на Python.',
				duration: 10,
				unavailable: false,
			},
			{
				id: 2,
				title: 'Графический дизайнер',
				description: 'Описание: Научим делать бренды узнаваемыми через создание логотипов, графики для рекламы, упаковки и не только.',
				duration: 6,
				unavailable: false,
			},
			{
				id: 3,
				title: 'Веб-разработчик',
				description: 'Описание: Веб-разработчик создаёт сайты, сервисы и приложения, которыми мы ежедневно пользуемся.',
				duration: 7,
				unavailable: false,
			},
			{
				id: 4,
				title: 'Инженер по тестированию',
				description: 'Описание: Вы научитесь находить ошибки в работе сайтов и приложений с помощью Java, JavaScript или Python.',
				duration: 7,
				unavailable: false,
			},
			{
				id: 5,
				title: 'Бухгалтер',
				description: 'Описание: Нет данных',
				duration: 6,
				unavailable: true,
			},
			{
				id: 6,
				title: 'Специалист по кибербезопасности',
				description: 'Описание: Нет данных',
				duration: 2,
				unavailable: true,
			},
			{
				id: 7,
				title: 'Backend-разработчик',
				description: 'Описание: Нет данных',
				duration: 9,
				unavailable: true,
			},
		];
		
		cardsIsLoading.value = false;
	}, 2000)
};
cardsLoading()

const defaultCardObject = ref({
	id: 0,
	title: '',
	description: '',
	duration: '',
	unavailable: false,
});

const showModal = (condition) => { show.value = ref( condition )};
const openCardForEdit = (card) => {
	if (card) defaultCardObject.value = { ...card };
	showModal(true);
};

const updatedCard = (card) => { defaultCardObject.value = card };

const saveCard = () => {
	cardsIsLoading.value = true;
	setTimeout(() => {
		const newCard = Object.assign({}, defaultCardObject.value);
		cards.value = cards.value.map(element => element.id === newCard.id ? newCard : element);
		
		cardsIsLoading.value = false;
	}, 600)
};

</script>

<style scoped>
@import './assets/global.css';
.modal-window {
	position: absolute;
	z-index: 100;
	top: 150px;
	left: calc((100% - 45vw)/2);
  }
</style>