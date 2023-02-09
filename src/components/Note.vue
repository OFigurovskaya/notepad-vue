<script>
import Like from './Like.vue';
import Dislike from './Dislike.vue';
let value = localStorage.getItem('key');
let value2 = JSON.parse(value);


export default {
    name: 'Note',
    data() {
        return {
            notes: value2 ? value2 : [],
            message: '',
            search: '',
            placeholder: 'Введите текст',
        }
    },
    components: {
        Like,
        Dislike,
    },
    methods: {
        save() {
            this.notes.push(this.message);
            console.log(this.message);
            this.message = '';
            let json = JSON.stringify(this.notes);
            localStorage.setItem('key', json);

        },
        edit(index) {
            this.message = (this.notes[index]);
            this.notes.splice(index, 1);
        },
        remove(index) {
            this.notes.splice(index, 1);
            let json = JSON.stringify(this.notes);
            localStorage.setItem('key', json);
        },
        reset() {
            let list = document.querySelectorAll('li');
            for (let li of list) {
                li.classList.remove('red');
            }
        }

    },
    computed: {
        getSearch() {
            let list = document.querySelectorAll('li');
            for (let li of list) {
                if (li.textContent.indexOf(this.search) != -1) {
                    li.classList.add('red');
                }
            }
            this.search = '';
        },

    }
}
</script>

<template>
    <div class="wrapper-note" :class="{ flex: true }">
        <div :class="{five: true}">
            <div>
                <textarea v-model="message" @keyup.enter="save" :class="{ field: true }" :placeholder="placeholder"></textarea>
                <button @click="save" :class="{ btn: true, save: true }">save</button>
            </div>
            <ul v-for="(note, index) in notes" :key="index">
                <li @click="edit(index)" :class="{list: true}">{{ note }}</li>
                <button @click="remove(index)" :class="{del: true}">delete</button>
            </ul>
            <div :class="{likes: true}">
                <Like :class="{empty: true}"/>
                <Dislike :class="{empty: true}"/>
            </div>
        </div>
        <div>
            <input v-model="search" :class="{ search: true }">
            <button @click="getSearch" :class="{ search: true, btn: true }">&#128269;</button>
            <button @click="reset" :class="{ search: true, btn: true }">&#10060;</button>
        </div>
    </div>
</template>

<style>
.red {
    background-color: rgb(235, 106, 106);
}

.flex {
    display: flex;
    justify-content: space-around;
    position: static;
}

.field {
    padding: 5%;
    width: 30vw;
    height: 25vh;
    margin-bottom: 3vh;
    border-radius: 10px;
}

.search {
    height: 5vh;
    margin-bottom: 3vh;
    border-radius: 10px;
}

.btn {
    background-color: bisque;
    cursor: pointer;
}

.center {
    margin: 0 auto;
}

.save {
    font-weight: 600;
    padding: 3%;
    border-radius: 15px;
    left: 35%;
}

.list {
    list-style: none;
    display: inline-block;
    padding: 1%;
    border-radius: 10px;
    margin-right: 2%;
    border: 1px solid black;
    font-weight: 600;
    font-style: italic;
    margin-bottom: 2%;
}

.five {
    width: 50%;
}

.del {
    background-color: rgb(244, 219, 251);
    border: 1px solid black;
    border-radius: 5px;
    padding: 1%;
}

.likes {
    text-align: left;
}

.empty {
    background-color: transparent;
    border: none;
}
</style>