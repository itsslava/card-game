<script setup>
import { ref } from 'vue';
import RightIcon from '../icons/right-icon.vue';
import FalseIcon from '../icons/false-icon.vue';

const { cardNumber, cardValue, cardTranslation } = defineProps({
	cardNumber: {
		type: [String, Number],
		required: true,
	},
	cardValue: {
		type: String,
		required: true,
	},
	cardTranslation: {
		type: String,
		required: true,
	},
});

const isFlipped = ref(false);

function flipCard() {
	isFlipped.value = true;
}

function markWrong() {
	isFlipped.value = false;
}

function markRight() {
	isFlipped.value = false;
}
</script>

<template>
	<div class="card">
		<div class="card-frame">
			<p class="card-number">{{ cardNumber }}</p>
			<p class="card-value">
				{{ isFlipped ? cardTranslation : cardValue }}
			</p>
			<div class="card-footer">
				<button v-if="!isFlipped" type="button" class="card-button flip-button" @click="flipCard">
					Перевернуть
				</button>
				<template v-else>
					<div class="card-footer-buttons">
						<button type="button" class="card-button icon-button wrong" @click="markWrong">
							<FalseIcon />
						</button>
						<button type="button" class="card-button icon-button right" @click="markRight">
							<RightIcon />
						</button>
					</div>
				</template>
			</div>
		</div>
	</div>
</template>

<style scoped>
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
</style>
