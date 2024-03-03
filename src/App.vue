<template>
  <div class="container">
		<EditModal v-if="showModal" :card="cardForEdit" @show-modal="!showModal" @set-card="updatedCard" @save-card="saveCard"/>
		<h1 class="title">Список курсов</h1>
    <div class="training-list">
			<CardsDrawing :cards="cards" @click-by-card="openCardForEdit"/>
    </div>
  </div>
</template>

<script setup>
import EditModal from './components/EditModal.vue';
import CardsDrawing from './components/CardsDrawing.vue';
import { ref } from 'vue';

const cards = ref([
		{
			id: 1,
			title: 'Python-разработчик',
			description: 'Описание: На Python пишут сайты, приложения, игры и чат-боты. Netflix, Spotify, Google, Dropbox и Youtube написаны на Python.',
			duration: '10 месяцев',
			unavailable: false,
		},
		{
			id: 2,
			title: 'Графический дизайнер',
			description: 'Описание: Научим делать бренды узнаваемыми через создание логотипов, графики для рекламы, упаковки и не только.',
			duration: '6 месецев',
			unavailable: false,
		},
		{
			id: 3,
			title: 'Веб-разработчик',
			description: 'Описание: Веб-разработчик создаёт сайты, сервисы и приложения, которыми мы ежедневно пользуемся.',
			duration: '7 месецев',
			unavailable: false,
		},
		{
			id: 4,
			title: 'Инженер по тестированию',
			description: 'Описание: Вы научитесь находить ошибки в работе сайтов и приложений с помощью Java, JavaScript или Python.',
			duration: '7 месецев',
			unavailable: false,
		},
		{
			id: 5,
			title: 'Бухгалтер',
			description: 'Описание: Нет данных',
			duration: '6 месецев',
			unavailable: true,
		},
		{
			id: 6,
			title: 'Специалист по кибербезопасности',
			description: 'Описание: Нет данных',
			duration: '12 месецев',
			unavailable: true,
		},
		{
			id: 7,
			title: 'Backend-разработчик',
			description: 'Описание: Нет данных',
			duration: '9 месецев',
			unavailable: true,
		},
		]);

		
const showModal = ref(false);

// Объект для редактирования карточки
const cardForEdit = ref({
	id: 0,
	title: '',
	description: '',
	duration: '',
	unavailable: false,
});

// Функция для обновления данных редактируемой карточки
const updatedCard = (card) => cardForEdit.value = card;

// Функция для сохранения изменений в карточке
const saveCard = () => {
	const newCard = Object.assign({}, cardForEdit.value);
	cards.value = cards.value.map(el => el.id === newCard.id ? newCard : el);
};

// Функция для открытия карточки для редактирования
const openCardForEdit = (card) => {
	!showModal
	cardForEdit.value = Object.assign({}, card)
	};
</script>

<style scoped>
@import './assets/global.css';
</style>
