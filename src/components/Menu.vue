<template>

  <section class="menu">
    <div id="navigator">
      <button id="reset" v-if="!ganador" @click="$emit('restart')">New colors</button>
      <button id="reset" v-else @click="$emit('restart')">Play again!</button>
      <span id="message">{{message}}</span>

      <button id="easy" :class="{selected: !isHard }" @click="$emit('facil')">easy</button>
      <button id="hard" :class="{selected: isHard }" @click="$emit('dificil')">hard</button>
    </div>
  </section>

</template>

<script lang="js">

  export default  {
    name: 'menu',
    props: ['ganador', 'isHard', 'message'],
    mounted () {

    },
    data () {
      return {
        restartButton: document.querySelector("#reset"),
        easyButton: document.querySelector("#easy"),
        hardButton: document.querySelector("#hard")

      }
    },
    methods: {

    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .menu {

  }
#navigator {
  background: #ffffff;
  height: 30px;
  text-align: center;
  margin: 0;
  margin-top: -30px;
}
#message {
  color: #000000;
  display: inline-block;
  width: 20%;
}
button {
  border: none;
  background-color: white;
  font-family: "Montserrat", "Avenir";
  text-transform: uppercase;
  height: 100%;
  font-weight: 700;
  letter-spacing: 1px;
  color: steelblue;
  transition: all 0.3s;
  outline: none;
}
button:hover {
  color: white;
  background-color: steelblue;
}
.selected {
  background-color: steelblue;
  color: white;
}
</style>
