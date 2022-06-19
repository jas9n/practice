<template>
    <div id="stopwatch" class="h-screen flex flex-col justify-center items-center">
        <home-link class="hover:text-red-300"/>
        <h1 class="text-4xl text-red-300">Stopwatch</h1>
        <div id="time" class="p-6 flex justify-center items-center">
            <div class="w-72 flex justify-start items-center text-6xl text-end">
                <span id="minutes" class="mx-2">{{ minutesEl }}</span>
                <p>:</p>
                <span id="seconds" class="mx-2">{{ secondsEl }}</span>
                <p>:</p>
                <span id="milliseconds" class="mx-2">{{ millisecondsEl }}</span>
            </div>
        </div>
        <div id="buttons" class="p-2 flex justify-center items-center">
            <watch-btn @e="start()">Start</watch-btn>
            <watch-btn @e="stop()">Stop</watch-btn>
            <watch-btn @e="reset()">Reset</watch-btn>
        </div>
    </div>
</template>

<script>
export default {
    name: "Stopwatch",
    data() {
        return {
            milliseconds: 0,
            seconds: 0,
            minutes: 0,
            millisecondsEl: "00",
            secondsEl: "00",
            minutesEl: "00",
        }
    },
    created() {
        this.milliseconds = 0
        this.seconds = 0
        this.minutes = 0
        this.millisecondsEl = "00"
        this.secondsEl = "00"
        this.minutesEl = "00"
        this.interval
    },
    methods: {
        timer() {
            this.milliseconds++
            console.log(this.milliseconds)
            if (this.milliseconds <= 9) {
                this.millisecondsEl = "0" + this.milliseconds
            }
            if (this.milliseconds > 9) {
                this.millisecondsEl = this.milliseconds
            }
            if (this.milliseconds > 99) {
                this.milliseconds = 0
                this.seconds++
            }
            if (this.seconds <= 9) {
                this.secondsEl = "0" + this.seconds
            }
            if (this.seconds > 9) {
                this.secondsEl = this.seconds
            }
            if (this.seconds > 59) {
                this.seconds = 0
                this.minutes++
            }
            if (this.minutes <= 9) {
                this.minutesEl = "0" + this.minutes
            }
            if (this.minutes > 9) {
                this.minutesEl = this.minutes
            }
        },
        start() {
            clearInterval(this.interval)
            this.interval = setInterval(this.timer,10);
        },
        stop() {
            clearInterval(this.interval)
        },
        reset() {
            clearInterval(this.interval)
            this.milliseconds = 0
            this.seconds = 0
            this.minutes = 0
            this.millisecondsEl = "00"
            this.secondsEl = "00"
            this.minutesEl = "00"
        },
    }
}
</script>