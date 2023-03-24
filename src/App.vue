<template>
    <div class="container">

        <div v-for="counter in counters" v-bind:key="counter.id" class="counter">
            <Counter :params="counter.params"/>
        </div>
        <AddBtn @click="addCounter"/>

    </div>
    
</template>

<script>
import Counter from './components/Counter.vue';
import AddBtn from './components/AddBtn.vue'
export default {
    name: "App",
    components: {
        Counter: Counter,
        AddBtn: AddBtn,
    },
    data() {
        return {
            counters: [
                {
                    id: 1,
                    params: {
                        sec: 40,
                        min: 2,
                        hrs: 0,
                    }
                },
                {
                    id: 2,
                    params: {
                        sec: 32,
                        min: 23,
                        hrs: 0,
                    }
                },
                {
                    id: 3,
                    params: {
                        sec: 15,
                        min: 30,
                        hrs: 1,
                    }
                },
                {
                    id: 4,
                    params: {
                        sec: 33,
                        min: 20,
                        hrs: 1,
                    }
                }
            ]
        }
    },
    methods: {
        addCounter() {
            this.counters.push(
                {id: Date.now(), 
                    params: {
                        sec: 0,
                        min: 0,
                        hrs: 0,
            }})
        }
    }
}
</script>


