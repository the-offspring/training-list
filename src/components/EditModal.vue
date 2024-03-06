<template>
	<transition name="modal">
	  <div class="modal-shadow">
		<form @submit.prevent="save" class="modal-form">
		  <div class="modal__header">
			<h5 class="modal-title">Редактирование курса</h5>
			<button type="click" class="modal-close" @click="emit('show-modal', false)">&#10006;</button>
		  </div>
		  <div class="modal__body">
			<div class="body-text-edit">
			  <label class="text-edit_lable">Название курса:</label>
			  <input type="text" :value="card.title" @input="editTitle">
			  <label class="text-edit_lable">Описание курса:</label>
			  <input type="text" :value="card.description" @input="editDescription">
			  <label class="text-edit_lable">Длительность курса:</label>
			  <input type="number" :value="card.duration" @input="editDuration">
			</div>
			<div class="body-text-settings">
			  <input type="checkbox" :value="card.unavailable = !card.unavailable" @input="editUnavailable">
			  <label class="text-settings_lable">Сделать курс {{ card.unavailable ? 'доступным' : 'недоступным' }}</label>
			</div>
		  </div>
		  <div class="modal__footer">
			<button type="submit">Сохранить</button>
			<button type="reset" @click="emit('show-modal', false)">Отмена</button>
		  </div>
		</form>
	  </div>
	</transition>
  </template>
  
  <script setup>
  const { card } = defineProps({
	card: {
	  type: Object,
	  default: null,
	},
  });
  
  const emit = defineEmits(['save-card', 'show-modal']);
  
  const edit = (property, event) => {
	const data = { ...card };
	data[property] = event.target.value;
	emit('set-card', data);
  };
  
  const editTitle = (event) => edit('title', event);
  const editDescription = (event) => edit('description', event);
  const editDuration = (event) => edit('duration', event);
  const editUnavailable = (event) => edit('unavailable', event);
  
  const save = () => {
	const data = { ...card };
	emit('save-card', data);
	emit('show-modal', false);
  };
  </script>
  
  
  <style scoped>
  .modal-enter-active {
	transition: all .3s ease;
  }
  .modal-leave-active {
	transition: all .8s cubic-bezier(1.0, 0.5, 0.8, 1.0);
  }
  .modal-enter, .modal-leave-to {
	transform: translateX(10px);
	opacity: 0;
  }
  </style>
  