<template>
  <div id="app">
    <body>
      <Header :colorDisplay="pickedColor" :ganador="ganador"/>
      <!-- Con ":" es la prop que va a recibir el hijo. Con "@" es lo que está escuchando 
      el padre. Si el hijo manda un $emit lo recibe así. Luego lo que está entre comillas es
      lo que va a hacer, en este caso tira el método restart() -->
      <Menu :ganador="ganador" :isHard="isHard" :message="messageDisplay" @restart="restart" @dificil="ponerDificil" @facil="ponerFacil"/>
      <Main :squaresBColors="colors" :pickedColor="pickedColor" :ganador="ganador" @colorSeleccionado="verificarGanador"/>
    </body>
  </div>
</template>

<script>
import Menu from './components/Menu.vue'
import Main from './components/Main.vue'
import Header from './components/Header.vue'

export default {
  name: 'App',
  components: {
    Header,
    Menu,
    Main
  },
  data () {
    return {
      colorCount: 6,
      isHard: true,
      colors: [],
      pickedColor: "",
      ganador: false,
      squares: [],
      messageDisplay: ""
    }
  },
  beforeMount(){
    this.colors = this.createNewColors(this.colorCount);
    this.pickedColor = this.colors[this.pickColor()];
    this.squares.length = this.colorCount;
    console.log(this.colors[3]);
  },
  methods: {
    restart(){
      this.colors = this.createNewColors(this.colorCount);
      this.pickedColor = this.colors[this.pickColor()];
      this.messageDisplay = "";
      this.ganador = false;
      /*this.textContent = "Pick New Colors!";
      this.header.style.backgroundColor = "steelblue";
      this.messageDisplay.textContent = "";
      this.restartButton.textContent = "New Colors!";
      for (var i = 0; i <this.squares.length; i++) {
        this.squares[i].style.backgroundColor = this.colors[i];
      }*/
    },
    pickColor(){
      let quantity;
      if (this.ganador) {
        quantity = 6;
      } else {
        quantity = 3;
      }

      return Math.floor(Math.random() * quantity);
    },
    createNewColors(numbers){
      let arr = [];
      for (let i = 0; i < numbers; i++) {
        arr.push(this.createRandomStringColor());
      }
        return arr;
    },
    randomInt(){
      return Math.floor(Math.random() * 256);
    },
    createRandomStringColor(){
      return "rgb(" + this.randomInt() + ", " + this.randomInt() + ", " + this.randomInt() + ")" ;
    },
    ponerFacil(){
      if (this.isHard) {
        this.isHard = false;
        this.colorCount = 3;
        /*for (let i = 0; i < this.colorCount; i++) {
          this.squares[(i+3)].style.display = "none";
        }*/
        this.restart();
      }
    },
    ponerDificil(){
      if (!this.isHard) {
        this.isHard = true;
        this.colorCount = 6;
        this.restart();
        /*for (let i = 3; i < this.colorCount; i++) {
          this.squares[i].style.display = "block";
        }*/
      }
    },
    verificarGanador(clickedColor){
      if (clickedColor === this.pickedColor) {
        this.ganador = true;
        this.messageDisplay = "You Picked Right!";
      } else {
        this.messageDisplay = "Try Again!";
        this.colors[this.colors.findIndex(color => clickedColor === color)] = "rgb(23, 23, 23)"
      }
    }
  },
  computed:{
  }
      
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body {
  background: #232323;
  margin: 0;
  font-family: "Montserrat", "Avenir";
}
</style>
