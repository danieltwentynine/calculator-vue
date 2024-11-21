<script setup>
const props = defineProps(['num1', 'num2', 'getNum1', 'getNum2', 'getOperation', 'answer']);
</script>

<template>
    <form @submit.prevent>
        <div class="text-center mt-5">
            <input :value="props.num1" @input="props.getNum1" type="number" class="p-2" placeholder="0" required />
            <input :value="props.num2" @input="props.getNum2" type="number" class="p-2 ms-2" placeholder="0" required />
        </div>
        <div class="text-center mt-4">
            <select @input="props.getOperation" class="p-1">
                <option value="+">+</option>
                <option value="-">-</option>
                <option value="*">*</option>
                <option value="/">/</option>
            </select>
        </div>
        <div class="answer text-center m-auto mt-5"
            :style="{ width: `${Math.max(30, props.answer.toString().length * 2)}%` }">
            {{ props.answer !== null ? props.answer : 'Result will appear here' }}
        </div>
    </form>
</template>

<style scoped>
.answer {
    background-color: rgb(225, 225, 225);
    height: 150px;
    min-width: 150px;
    max-width: 90%;
    border-radius: 16px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.5rem;
    transition: width 0.3s ease;
    /* Smoothly animate the width changes */
}
</style>