<template>

  <section class="main">
    <div id="container">
      <div class="square" v-for="(squaresBColor, index) in squaresBColors" :key="index" 
      :style="{backgroundColor: ganador ? pickedColor : squaresBColor}" @click="enviarColor(squaresBColor)"></div>
    </div>
  </section>

</template>

<script lang="js">

  export default  {
    name: 'main',
    props: ['squaresBColors', 'pickedColor', 'ganador'],
    beforeMount(){

    },
    mounted () {

    },
    data () {
      return {
        colorCount: 6,
        isHard: true,
        colors: [],
        messageDisplay: "",
      }
    },
    methods: {
      enviarColor(clickedColor){
        this.$emit('colorSeleccionado', clickedColor);
      },
      setAllColorsTo(color) {
        this.squaresBColors.forEach(function (square){
          square.style.backgroundColor = color;
        })
      }      
    },
    computed: {
    }
}


</script>

<style scoped lang="css">
.juego {
}

.square {
  width: 30%;
  background: blue;
  padding-bottom: 30%;
  float: left;
  margin: 1.66%;
  border-radius: 10%;
  transition: background 0.8s;
  -webkit-transition: background 0.8s;
  -moz-transition: background 0.8s;
}
#container {
  margin: 20px auto;
  max-width: 600px;
}
</style>
