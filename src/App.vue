<template>
    <div class="container">

        <div v-for="counter in counters" v-bind:key="counter.id" class="counter">
            <Counter />
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
                },
                {
                    id: 2,
                },
                {
                    id: 3,
                },
                {
                    id: 4,
                }
            ]
        }
    },
    methods: {
        addCounter() {
            this.counters.push({id: Date.now()})
        }
    }
}
</script>


