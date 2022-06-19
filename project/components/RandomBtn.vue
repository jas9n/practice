<template>
    <button @click="$emit('e')" id="randomButton" class="rounded-lg w-40 h-16 z-20 flex justify-center items-center text-white cursor-pointer ease-in duration-150 hover:bg-white hover:text-black">
        <p class="text-md">Generate</p>
    </button>
</template>

<script>
export default {
    name: "RandomButton"
}
</script>