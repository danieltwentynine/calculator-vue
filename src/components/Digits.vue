<script setup>
    const props = defineProps([''])
</script>

<template>
    <div class="text-center mt-5">
        <input type="number" class="p-2">
        <input type="number" class="p-2 ms-2">
    </div>
    <div class="text-center mt-4">
        <select name="" id="" class="p-1">
            <option value="+">+</option>
            <option value="-">-</option>
            <option value="*">*</option>
            <option value="/">/</option>
        </select>
    </div>
    <div class="text-center mt-4">
        <button type="submit" class="btn btn-dark p-2">Calculate</button>
    </div>
</template>