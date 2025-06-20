<!-- Card.vue -->
<script setup>
import RightIcon from '../icons/right-icon.vue';
import FalseIcon from '../icons/false-icon.vue';

defineProps({
	card: Object,
	index: Number,
});
const emit = defineEmits(['flip', 'wrong', 'right']);
</script>

<template>
	<div class="card" :class="`status-${card.status}`">
		<div class="card-frame">
			<p class="card-number">{{ card.number }}</p>
			<p class="card-value">
				{{ card.state === 'closed' ? card.word : card.translation }}
			</p>
			<div class="card-footer">
				<button
					v-if="card.state === 'closed'"
					class="card-button flip-button"
					@click="emit('flip', index)"
				>
					Перевернуть
				</button>
				<template v-else>
					<div class="card-footer-buttons">
						<button class="card-button icon-button" @click="emit('wrong', index)">
							<FalseIcon />
						</button>
						<button class="card-button icon-button" @click="emit('right', index)">
							<RightIcon />
						</button>
					</div>
				</template>
			</div>
		</div>
	</div>
</template>

<style scoped>
.card-list {
	display: flex;
	gap: 16px;
	flex-wrap: wrap;
}
.card {
	position: relative;
	width: 250px;
	height: 376px;
	background-color: var(--color-white);
	border-radius: 16px;
	box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.1);
}

.card-frame {
	position: absolute;
	top: 20px;
	left: 19px;
	width: 212px;
	height: 337px;
}

.card-frame::before {
	content: '';
	position: absolute;
	top: 8px;
	left: 0;
	width: 212px;
	height: 320px;
	background-color: var(--color-white);
	border: 1px solid var(--color-secondary);
	border-radius: 12px;
}

.card-number {
	position: absolute;
	top: 0;
	left: 16px;
	margin: 0;
	font-size: 14px;
	color: var(--color-black);
	background-color: var(--color-white);
}

.card-value {
	position: absolute;
	top: 156px;
	left: 16px;
	width: 180px;
	margin: 0;
	font-size: 18px;
	color: var(--color-black);
	text-align: center;
	line-height: 22px;
}

.card-footer {
	position: absolute;
	top: 319px;
	left: 50%;
	transform: translateX(-50%);
	width: 97px;
	display: flex;
	justify-content: space-between;
	align-items: center;
	background-color: var(--color-white);
	padding: 0;
}

.card-footer-buttons {
	position: absolute;
	top: -7px;
	background-color: var(--color-white);
	display: flex;
	justify-content: space-between;
	align-items: center;
	width: 100%;
}

.card-button {
	background: none;
	border: none;
	margin: 0;
	padding: 0;
	cursor: pointer;
}

.card-button.flip-button {
	width: 97px;
	height: 18px;
	line-height: 18px;
	font-size: 12px;
	font-weight: 700;
	color: var(--color-black);
	text-transform: uppercase;
	background-color: var(--color-white);
}

.icon-button {
	width: 32px;
	height: 32px;
	display: flex;
	align-items: center;
	justify-content: center;
	padding: 0;
	border-radius: 50%;
}

.card.status-success {
	border: 2px solid #2ecc71;
}
.card.status-fail {
	border: 2px solid #e74c3c;
}
.card.status-pending {
	border: 2px solid transparent;
}
</style>
