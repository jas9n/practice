<template>
    <div id="colorRandomizer" class="bg-black h-screen flex flex-col justify-center items-center">
        <home-link class="text-white hover:text-gray-300"/>
        <h1 id="title" class="text-4xl text-white text-center">Random Color Generator</h1>
        <div id="screen" class="bg-indigo-300 w-64 h-64 m-4 rounded-xl flex flex-col justify-center items-center ease-in-out duration-300">
            <p id="rgb" class="text-lg text-black">{{ rgb }}</p>
            <p id="hex"></p>
        </div>
        <div @click="randomize()" id="button" class="bg-black rounded-lg w-40 h-16 flex justify-center items-center text-white cursor-pointer ease-in duration-150 hover:bg-white hover:text-black">
            <p class="text-md">Randomize</p>
        </div>
    </div>
</template>

<script>
export default {
    name:"ColorRandomizer",
    data() {
        return {
            colors: [
                // #F3A4A4,
                // #F7C9CA,
                // #FDE68A,
                // #A7F3D0,
                // #93C5FC,
                // #BFDBFD,
                // #A5B4FC,
                // #C7D2FD,
                // #C4B5FD,
                // #F2A7D4,
                // #F2A7D4
            ],
            rgb: "",
            hex: ""
        }
    },
    created() {
        this.colors = []
        while (this.colors.length < 100000) {
            this.colors.push(`rgb(${Math.floor((Math.random() * 255) + 1)}, ${Math.floor((Math.random() * 255) + 1)}, ${Math.floor((Math.random() * 255) + 1)})`)
        }
        this.rgb = "rgb(165, 180, 252)"
        this.hex = ""
    },
    methods: {
        randomize() {
            this.rgb = this.colors[Math.floor((Math.random() * 100) + 1)]
            document.querySelector("#screen").style.backgroundColor = this.rgb
            // this.getHex()
            // this.rgbToHex()
            // console.log(rgbToHex(21, 21, 21))
        },
        // getHex(c) {
        //     let hex = c.toString(16);
        //     return hex.length == 1 ? "0" + hex : hex;
        // },
        // rgbToHex(r, g, b) {
        //     this.getHex()
        //     return "#" + getHex(r) + getHex(g) + getHex(b);
        // }
        
    }
}
</script>