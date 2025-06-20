<script setup>
import Header from './components/header.vue';
import CardList from './components/card-list.vue';
</script>

<template>
	<div class="container">
		<Header />
		<div class="card-container">
			<CardList />
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
