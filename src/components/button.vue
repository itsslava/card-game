<script setup></script>
<template>
	<button class="button"><slot /></button>
</template>
<style scoped>
.button {
	width: 335px;

	text-align: center;
	font-size: 24px;
	color: var(--color-white);

	border: none;
	border-radius: 100px;
	padding: 16px 0;
	cursor: pointer;
	background-color: var(--color-primary);
}

.button:hover {
	background-color: var(--color-primary-hover);
	transition: all 0.3s ease;
}
</style>
