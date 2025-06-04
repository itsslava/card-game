<script setup>
import Header from './components/header.vue';
import Card from './components/card.vue';
</script>

<template>
	<div class="container">
		<Header />
		<div class="card-container">
			<Card card-number="01" card-value="unadmitted" card-translation="неопознанный" />
		</div>
	</div>
</template>

<style scoped>
.container {
	display: flex;
	flex-direction: column;

	padding: 0 62px;
}

.card-container {
	display: grid;
}
</style>
