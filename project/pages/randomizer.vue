<template>
    <div id="colorRandomizer" class="bg-indigo-300 h-screen flex flex-col justify-center items-center ease-in-out duration-300">
        <div id="overlay" class="absolute z-0 bg-black opacity-75 h-screen w-screen"></div>
        <home-link class="text-white z-10 hover:text-gray-300"/>
        <h1 id="title" class="text-4xl text-white text-center z-10">Random Color</h1>
        <div id="screen" class="bg-indigo-300 w-64 h-64 m-4 z-20 rounded-xl flex flex-col justify-center items-center ease-in-out duration-300">
        </div>
        <p id="rgb" class="text-lg text-indigo-300 z-10 pb-4">{{ rgb }}</p>
        <random-btn @e="randomize()"/>
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
            document.querySelector("#colorRandomizer").style.backgroundColor = this.rgb
            document.querySelector("#screen").style.backgroundColor = this.rgb
            document.querySelector("#rgb").style.color = this.rgb
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