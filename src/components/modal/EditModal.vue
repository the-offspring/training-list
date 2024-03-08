<template>
	  
		<div class="card">
			<form @submit.prevent="saveCard" class="modal-form">
			  <div class="card-header modal__header">
				<h5 class="modal-title">Редактирование курса</h5>
				<button type="button" @click="closeModal">&#10006;</button>
			  </div>
			  <div class="card-body modal__body">
				<div class="body-text-edit">
				  <label class="text-edit_lable">Название курса:</label>
				  <input type="text" :value="card.title" @input="editTitle">
				  <label class="text-edit_lable">Описание курса:</label>
				  <textarea type="text" :value="card.description" @input="editDescription"></textarea>
				  <label class="text-edit_lable">Длительность курса:</label>
				  <input type="number" :value="card.duration" @input="editDuration">
				</div>
				<div class="body-text-settings">
					<label>
					  <input type="checkbox" :value="card.unavailable" @change="toggleUnavailable" @input="editUnavailable">
					<p class="text-settings_lable">Сделать курс {{ card.unavailable ? 'доступным' : 'недоступным' }}</p>
				  </label>
				</div>
			  </div>
			  <div class="modal-footer">
				<button type="submit">Сохранить</button>
				<button type="button" @click="closeModal">Отмена</button>
			  </div>
			</form>
		</div>

</template>
  
<script setup>

const prop = defineProps({
    card: {
        type: Object,
        default: null,
    },
    showModal: {
        type: Function,
    },
});

const emit = defineEmits(['save-card', 'set-card']);

const closeModal = () => {
    prop.card.value = null;
    prop.showModal(false);
};

const editCard = (property, event) => {
    const data =  Object.assign({}, prop.card)
    data[property] = event.target.value;
    emit('set-card', data); 
}

const editTitle = (event) => editCard('title', event);
const editDescription = (event) => editCard('description', event);
const editDuration = (event) => editCard('duration', event);
const editUnavailable = (event) => editCard('unavailable', event);

const toggleUnavailable = () => {
	console.log("1",prop.card.unavailable)
    card.unavailable = !card.unavailable;
	console.log("2", prop.card.unavailable)

};

const saveCard = () => {
    emit('save-card');
    prop.showModal(false);
};

</script>

<style scoped>
  input, textarea {
	outline: 1px solid #c5c5c5;
	border: none;
	border-radius: 10px;
  }
  button {
	outline: 1px solid #c5c5c5;
	border: none;
	border-radius: 10px;
  }

  .card {
	min-width: 45vw;
  }
  .modal__header {
	display: flex;
	justify-content: space-between;
  }
  .body-text-edit {
	display: flex;
	flex-direction: column;
  }

  .modal-footer {
	padding: 8px 16px 12px;
	gap: 15px;
  }
  label {
	display: flex;
	gap: 15px;
	width: fit-content;
	margin-top: 15px;
	cursor: pointer;
	input {
			cursor: pointer;
			margin-block: auto;
			height: fit-content;
		}
		p {
			margin: 0;
		}
  }
  /* .modal-enter-active {
	transition: all .3s ease;
  }
  .modal-leave-active {
	transition: all .8s cubic-bezier(1.0, 0.5, 0.8, 1.0);
  }
  .modal-enter, .modal-leave-to {
	transform: translateX(10px);
	opacity: 0;
  } */
</style>
  