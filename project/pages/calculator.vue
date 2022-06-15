<template>
    <div id="calculator" class="h-screen flex flex-col justify-center items-center">
        <h1 class="text-4xl px-3">Calculator</h1>
        <div id="screen" class="h-24 w-64 py-4 flex justify-end items-end">
            <p class="text-2xl tracking-widest">{{ screen }}</p>
        </div>
        <div id="buttons" class="grid grid-cols-4 grid-rows-5 gap-4">
            <!-- <calc-btn v-for="button in buttons" :key="button.index" class="p-2">{{ button }}</calc-btn> -->
            <!-- first row -->
            <calc-btn @e="display('(')">(</calc-btn>
            <calc-btn @e="display(')')">)</calc-btn>
            <calc-btn @e="display('%')">%</calc-btn>
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
            <calc-btn @e="display('x')">x</calc-btn>
            <!-- fourth row -->
            <calc-btn @e="display('1')">1</calc-btn>
            <calc-btn @e="display('2')">2</calc-btn>
            <calc-btn @e="display('3')">3</calc-btn>
            <calc-btn @e="display('-')">-</calc-btn>
            <!-- fifth row -->
            <calc-btn @e="display('0')">0</calc-btn>
            <calc-btn @e="display('.')">.</calc-btn>
            <calc-btn @e="evaluate()">=</calc-btn>
            <calc-btn @e="display('+')">+</calc-btn>
        </div>
    </div>
</template>

<script>
export default {
    name: "Calculator",
    data() {
        return {
            // can't use this method because  buttons have different functions
            // buttons: ["(", ")", "%", "AC", "7", "8", "9", "/", "4", "5,", "6", "x", "1", "2", "3", "-", "0", ".", "=", "+"]
            screen: "",
            calc: "",
            answer: "",

            // calc: "",
        }
    },
    created() {
        this.screen = "";
        this.calc = "";
        this.answer = "";
    },
    methods: {
        display(i) {
            this.screen += i;
        },
        evaluate() {
            this.calc = this.screen.value
            this.answer = eval(this.calc)
            console.log(this.screen.value)
        },
        clear() {
            this.screen = "";
            this.x = "";
            this.calc = "";
        }
    }
}
</script>