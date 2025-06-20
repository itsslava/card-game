<script setup>
import { ref } from 'vue';
import Card from './Card.vue';

const cards = ref([
	{
		number: '01',
		word: 'unadmitted',
		translation: 'непринятый',
		state: 'closed',
		status: 'pending',
	},
	{
		number: '02',
		word: 'rely',
		translation: 'полагаться',
		state: 'closed',
		status: 'pending',
	},
]);

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
</script>

<template>
	<div class="card-list">
		<Card
			v-for="(card, index) in cards"
			:key="card.number"
			:card="card"
			:index="index"
			@flip="flipCard"
			@wrong="markWrong"
			@right="markRight"
		/>
	</div>
</template>

<style scoped>
.card-list {
	display: flex;
	gap: 16px;
	flex-wrap: wrap;
}
</style>
