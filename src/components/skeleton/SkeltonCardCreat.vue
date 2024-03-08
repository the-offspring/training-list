<template>
	<div class="card card_skeleton">
		<div class="card-header">
			<h3 class="card__title skeleton"></h3>
		</div>
		<div class="card-body">
			<p class="card__text skeleton"></p>
			<p class="card__text skeleton"></p>
			<p class="card__text skeleton"></p>
			<div class="card-footer">
				<span class="card__duration skeleton"></span>
			</div>
		</div> 
	</div>
</template>

<script setup>

</script>

<style scoped>
.card {
	width: 100%;
  height: 200px;
	padding: 15px 24px 16px;
	border-radius: 16px;
}

.card__title {
	width: 60%;
  height: 30px;
	display: block;
	margin-block: 5px;
}
.card__text {
  height: 15px;
  display: block;
  margin-bottom: 4px;
  &:nth-child(1) {
    width: 90%;
  }
  &:nth-child(2) {
    width: 85%;
  }
  &:nth-child(3) {
    width: 50%;
  }
}

.card__duration {
	width: 25%;
  height: 10px;
	display: inline-block;
	/* padding: 2px 6px; */
	border-radius: 4px;
}

.card_skeleton {
	position: relative;
  cursor: default;
}

.card_skeleton::after {
  background-image: linear-gradient(
    318deg,
    #acacac 0%, #acacac 35%,
    #e4e4e4 50%, #e4e4e4 50%,
    #acacac 60%, #acacac 100%
  );
  background-size: 400%;
  animation: card_skeleton 3100ms infinite;
  content: '';
  z-index: 2;
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  border-radius: 16px;
}

@keyframes card_skeleton {
  from {background-position: 100% 100%;}
  to {background-position: 0 0;}
}

.skeleton {
  position: relative;
  cursor: default;
 }

.skeleton::after {
  background-image: linear-gradient(
    90deg,
    #e4e4e4 0%, #e4e4e4 40%,
    #acacac 50%, #acacac 55%,
    #e4e4e4 65%, #e4e4e4 100%
  );
  background-size: 400%;
  animation: skeleton 3000ms infinite;
  content: '';
  z-index: 6;
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  border-radius: 5px;
}

@keyframes skeleton {
  from {background-position: 100% 100%;}
  to {background-position: 0 0;}
}
</style>