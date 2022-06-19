<template>
    <div @click="$emit('e')" id="watchbtn" class="rounded-lg mx-2 w-24 h-12 flex justify-center items-center cursor-pointer ease-in duration-150 hover:bg-red-300 hover:text-black md:w-28 h-14">
        <p class="text-md"><slot></slot></p>
    </div>
</template>

<script>
export default {
    name: "StopwatchBtn",
}
</script>