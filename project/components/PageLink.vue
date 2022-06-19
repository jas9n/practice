<template>
    <div id="link" class="rounded-lg w-36 h-16 flex justify-center items-center text-center ease-in duration-150 hover:text-black">
        <p class="text-md"><slot></slot></p>
    </div>
</template>

<script>
export default {
    name: "PageLink",
}
</script>