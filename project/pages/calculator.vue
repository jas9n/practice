<template>
    <div id="calculator" class="h-screen flex flex-col justify-center items-center">
        <home-link class="hover:text-purple-300"/>
        <h1 class="text-4xl px-3 text-purple-300">Calculator</h1>
        <div id="screen" class="h-24 pt-8 flex justify-center items-center">
            <p class="text-2xl tracking-widest">{{ screen }}</p>
        </div>
        <div id="buttons" class="grid grid-cols-4 grid-rows-5 gap-4">
            <!-- <calc-btn v-for="button in buttons" :key="button.index" class="p-2">{{ button }}</calc-btn> -->
            <!-- first row -->
            <calc-btn @e="display('(')">(</calc-btn>
            <calc-btn @e="display(')')">)</calc-btn>
            <calc-btn @e="display('/100')">%</calc-btn>
            <calc-btn @e="clear()">AC</calc-btn>
            <!-- second row -->
            <calc-btn @e="display('7')">7</calc-btn>
            <calc-btn @e="display('8')">8</calc-btn>
            <calc-btn @e="display('9')">9</calc-btn>
            <calc-btn @e="display('/')">/</calc-btn>
            <!-- third row -->
            <calc-btn @e="display('4')">4</calc-btn>
            <calc-btn @e="display('5')">5</calc-btn>
            <calc-btn @e="display('6')">6</calc-btn>
            <calc-btn @e="display('*')">*</calc-btn>
            <!-- fourth row -->
            <calc-btn @e="display('1')">1</calc-btn>
            <calc-btn @e="display('2')">2</calc-btn>
            <calc-btn @e="display('3')">3</calc-btn>
            <calc-btn @e="display('-')">-</calc-btn>
            <!-- fifth row -->
            <calc-btn @e="display('0')">0</calc-btn>
            <calc-btn @e="display('0.')">.</calc-btn>
            <calc-btn @e="evaluate()">=</calc-btn>
            <calc-btn @e="display('+')">+</calc-btn>
        </div>
    </div>
</template>

<script>
import HomeLink from '../components/HomeLink.vue';
export default {
  components: { HomeLink },
    name: "Calculator",
    data() {
        return {
            // can't use this method because buttons have different functions
            // buttons: ["(", ")", "%", "AC", "7", "8", "9", "/", "4", "5,", "6", "x", "1", "2", "3", "-", "0", ".", "=", "+"]
            screen: "",
            answer: "",

        }
    },
    created() {
        this.screen = "";
        this.answer = "";
    },
    methods: {
        display(i) {
            this.screen += i;
        },
        evaluate() {
            // console.log(typeof this.answer)
            if (typeof eval(this.screen) === 'number') {
                this.answer = Math.round((eval(this.screen) + Number.EPSILON) * 1000000) / 1000000
                this.screen = this.answer
            } else {
                this.screen = "undefined"
            }
        },
        clear() {
            this.screen = "";
        }
    }
}
</script>