<template>
    <button @click="$emit('e')" class="w-8 h-8 p-8 text-lg rounded-full flex justify-center items-center">
        <slot></slot>
    </button>
</template>

<script>
export default {
    name: "CalculatorButton",
}
</script>