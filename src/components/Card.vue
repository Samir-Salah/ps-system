<template>
    <div class="card-panel">
        <div class="card-header">
            <img src="@/images/ps.png" alt="" />
            <h2>{{ customerName }}</h2>
        </div>
        <div class="card-timer container">
            <lable class="hours" ref="hours" id="hours">{{
                displayHours
            }}</lable>
            :
            <input
                th:field="*{cartTime.hours}"
                class="inp1"
                type="number"
                value=""
                hidden
            />
            <lable class="minutes" ref="minutes" id="minutes">{{
                displayMinutes
            }}</lable>
            :
            <input
                th:field="*{cartTime.minutes}"
                class="inp2"
                type="number"
                value=""
                hidden
            />
            <lable class="seconds" ref="seconds" id="seconds">{{
                displaySeconds
            }}</lable>
            <input
                th:field="*{cartTime.seconds}"
                type="number"
                class="inp3"
                value=""
                hidden
            />
        </div>
        <div class="card-timer-text">
            <span class="card-timer-text-hours">Hours</span>
            <span class="card-timer-text-minutes">Minutes</span>
            <span class="card-timer-text-seconds">Seconds</span>
        </div>
        <div class="card-btn-area">
            <button id="startStop" @click="startStop()">{{ startStopBtn }}</button>
            <button id="reset" @click="reset()">{{ resetBtn }}</button>
        </div>
        <div class="card-select-area">
            <div class="input-group mb-3">
                <select
                    class="card-select-players"
                    th:field="*{numberOfPlayer}"
                >
                    <option selected value="null"
                        >Select number of players</option
                    >
                    <option v-for="type in typesOfPlayers" :key="type.id">{{
                        type.typeName
                    }}</option>
                </select>
                <div class="input-group-append">
                    <label class="input-group-text" for="inputGroupSelect02"
                        >Players</label
                    >
                </div>
            </div>
            <div class="input-group mb-3">
                <select
                    class="card-select-devices"
                    id="inputGroupSelect02"
                    th:field="*{typeOfDevice}"
                >
                    <option selected value="null">Select Devices</option>
                    <option v-for="type in typeOfDevices" :key="type.id">{{
                        type.deviceName
                    }}</option>
                </select>
                <div class="input-group-append">
                    <label class="input-group-text" for="inputGroupSelect02"
                        >Device</label
                    >
                </div>
            </div>
        </div>
        <div class="card-action-btn">
            <div class="card-add-item">
                <img src="@/images/add-item.png" alt="" />
                <button class="card-add-item-btn">Add Item</button>
            </div>
            <div class="card-checkout">
                <img src="@/images/checkout.png" alt="" />
                <input
                    type="submit"
                    class="card-checkout-btn"
                    value="Checkout"
                />
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "Card",
    data: function() {
        return {
            customerName: "New Customer",
            displaySeconds: "00",
            displayMinutes: "00",
            displayHours: "00",
            seconds: 0,
            minutes: 0,
            hours: 0,
            interval: null,
            status: "stopped",
            startStopBtn: "Start",
            resetBtn: "Reset",
            typesOfPlayers: [
                {
                    id: 1,
                    typeName: "Single"
                },
                {
                    id: 2,
                    typeName: "Multi"
                }
            ],
            typeOfDevices: [
                {
                    id: 1,
                    deviceName: "Normal"
                },
                {
                    id: 2,
                    deviceName: "HD"
                },
                {
                    id: 3,
                    deviceName: "4K"
                }
            ]
        };
    },
    methods: {
        stopWatch() {
            this.seconds++;
            if (this.seconds / 60 === 1) {
                this.seconds = 0;
                this.minutes++;
                if (this.minutes / 60 === 1) {
                    this.minutes = 0;
                    this.hours++;
                }
            }
            if (this.seconds < 10) {
                this.displaySeconds = "0" + this.seconds.toString();
            } else {
                this.displaySeconds = this.seconds;
            }
            if (this.minutes < 10) {
                this.displayMinutes = "0" + this.minutes.toString();
            } else {
                this.displayMinutes = this.minutes;
            }
            if (this.hours < 10) {
                this.displayHours = "0" + this.hours.toString();
            } else {
                this.displayHours = this.hours;
            }
        },
        startStop() {
            if (this.status === "stopped") {
                this.interval = window.setInterval(this.stopWatch, 1000);
                this.startStopBtn = "Pause";
                this.status = "started";
            } else {
                window.clearInterval(this.interval);
                this.startStopBtn = "Start";
                this.status = "stopped";
            }
        },
        reset() {
            window.clearInterval(this.interval);
            this.seconds = 0;
            this.minutes = 0;
            this.hours = 0;
            this.displaySeconds = "00";
            this.displayMinutes = "00";
            this.displayHours = "00";
            this.startStopBtn = "Start";
        }
    }
};
</script>
