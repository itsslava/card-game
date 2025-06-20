<!-- eslint-disable no-undef -->
<script setup>
import { ref, onMounted } from 'vue';

import Header from './components/header.vue';
import CardList from './components/card-list.vue';

const API_ENDPOINT = 'http://localhost:8080/api/random-words';

const cards = ref([]);

async function getWords() {
	const res = await fetch(`${API_ENDPOINT}`);
	const data = await res.json();
	cards.value = data.map((item, i) => ({
		...item,
		number: i + 1 < 10 ? `0${i + 1}` : String(i + 1),
		state: 'closed',
		status: 'pending',
	}));
}

function flipCard(index) {
	cards.value[index].state = 'opened';
	cards.value[index].status = 'pending';
}

function markWrong(index) {
	cards.value[index].state = 'closed';
	cards.value[index].status = 'fail';
}

function markRight(index) {
	cards.value[index].state = 'closed';
	cards.value[index].status = 'success';
}

onMounted(getWords);
</script>

<template>
	<div class="container">
		<Header />
		<div class="card-container">
			<CardList :cards="cards" @flip="flipCard" @wrong="markWrong" @right="markRight" />
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
