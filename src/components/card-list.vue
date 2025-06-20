<script setup>
import Card from './card.vue';

const props = defineProps({
	cards: Array,
});

const emit = defineEmits(['flip', 'wrong', 'right']);
</script>

<template>
	<div class="card-list">
		<Card
			v-for="(card, index) in cards"
			:key="card.number"
			:card="card"
			:index="index"
			@flip="emit('flip', index)"
			@wrong="emit('wrong', index)"
			@right="emit('right', index)"
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
