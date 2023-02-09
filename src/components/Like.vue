<script>

let value = localStorage.getItem('count1');
let value2 = Number(JSON.parse(value));

export default {
    name: 'Like',
    data() {
        return {
            counter1: value2,
        }
    },
    methods: {
        count: function() {
            this.counter1++;
            let json = JSON.stringify(this.counter1);
            localStorage.setItem('count1', json);
        }
    },
    computed: {
        
    }
}
</script>

<template>
    <button @click="count">&#128154; {{ this.counter1 }}</button>
</template>