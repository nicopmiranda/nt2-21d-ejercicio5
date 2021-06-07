<template>

  <section class="header">
    <div id="header" :style="{backgroundColor: ganador ? colorDisplay : base}">
      <h1>The Great <br>
        <span id="colorDisplay">{{colorDisplay}}</span>
        <br>
        Guessing Game</h1>
    </div>
  </section>

</template>

<script lang="js">

  export default  {
    name: 'header',
    props: ['colorDisplay', 'ganador'],
    mounted () {

    },
    data () {
      return {
        base: 'steelblue'
      }
    },
    methods: {

    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .header {

  }
  #header {
    transition: all 0.3s;
    background: steelblue;
    text-transform: uppercase;
    text-align: center;
    margin: 0;
    color: white;
  }
  #colorDisplay {
    font-size: 200%;
  }

h1 {
  font-weight: normal;
  line-height: 1.1;
  padding: 20px 0;
}
</style>
