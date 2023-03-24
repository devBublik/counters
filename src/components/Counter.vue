
<template>
    <div class="counter" v-bind:class="{active : isActive }">
        <div class="counter__display">
            {{ time
            }}
        </div>
        <div class="counter__controls">
            <IconPause  v-if="isActive" @click="stop"/>
            <IconPlay v-else @click="start"/>
            <IconStop @click="reset"/>
        </div>
    </div>
</template>

<script>
import IconPlay from '../components/icons/IconPlay.vue';
import IconPause from '../components/icons/IconPause.vue';
import IconStop from './icons/IconStop.vue';
export default {
    name: 'Counter',
    components: {
        IconPlay: IconPlay,
        IconStop: IconStop,
        IconPause: IconPause,
    },
    data() {
        return {
            sec: 0,
            min: 0,
            hrs: 0,
            base: 60,
            t: 0,
            isActive: false

        }
    },
    computed: {
       time: function() {
            return (this.hrs > 9 ? this.hrs : "0" + this.hrs)
                + ":" + (this.min > 9 ? this.min : "0" + this.min)  
                + ":" + (this.sec > 9 ? this.sec : "0" + this.sec) 
        } 
    },  
    methods: {
        tick(){
            this.isActive = true
            this.sec++;
            if (this.sec >= this.base) {
                this.sec = 0;
                this.min++;
                if (this.min >=this.base) {
                    this.min = 0;
                    this.hrs++;
                }
            }
        },
        start() {
            this.tick();
            this.timer();
        },
        timer() {
            this.t = setInterval(this.tick, 1000);
        },
        stop() {
            this.isActive = false
            clearTimeout(this.t);
        },
        reset() {
            clearTimeout(this.t);
            this.isActive = false
            this.sec= 0
            this.min =0
            this.hrs = 0
        }
    }
}
</script>