<script setup>
import Score from './score.vue';
</script>
<template>
	<div class="header-container">
		<h1 class="header-title">Запомни слово</h1>
		<Score />
	</div>
</template>
<style scoped>
.header-container {
	display: flex;
	justify-content: space-between;
	align-items: center;

	padding-top: 36px;
	padding-bottom: 36px;
}

.header-title {
	text-transform: uppercase;
	font-size: 16px;
}
</style>
