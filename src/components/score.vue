<script setup>
import HeartIcon from '../icons/heart-icon.vue';

import { ref } from 'vue';

const score = ref('100');
</script>
<template>
	<div class="score-container">
		<div class="score-value">{{ score }}</div>
		<HeartIcon />
	</div>
</template>
<style scoped>
.score-container {
	background: var(--color-secondary);
	padding: 12px 24px;
	border-radius: 36px;
	box-shadow: 0px 0px 4px 0px rgba(0, 0, 0, 0.15);
	display: flex;
	align-items: center;
	gap: 10px;
}
.score-value {
	font-size: 16px;
	color: var(--color-primary);
	font-weight: 700;
}
</style>
