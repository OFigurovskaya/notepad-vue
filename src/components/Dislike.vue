<script>

let value = localStorage.getItem('count2');
let value2 = Number(JSON.parse(value));

export default {
    name: 'Dislike',
    data() {
        return {
            counter2: value2,
        }
    },
    methods: {
        count: function() {
            this.counter2++;
            let json = JSON.stringify(this.counter2);
            localStorage.setItem('count2', json);
        }
    },
    computed: {
        
    }
}
</script>

<template>
    <button @click="count">&#128078; {{ this.counter2 }}</button>
</template>