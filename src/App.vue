<script>
import Note from './components/Note.vue';
export default {
  name: 'App',
  data() {
    return {

    }
  },
  components: {
    Note,
  },
  methods: {

  },
  computed: {

  }
}
</script>

<template >
<div class="wrapper" :class="{main: true}">
  <Note />
</div>
</template>

<style>
.main {
  width: auto;
  height: auto;
  margin: 0 auto;
  border: 2px solid blue;
  border-radius: 20px;
  padding: 5%;
  background-color: beige;
  position: relative;
}
</style>