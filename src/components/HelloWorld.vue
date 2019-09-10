<template lang="pug">
  div
    | Willkommen
    br
    button(@click="activePlayer = 2") KKK
    button(class="startButton" @click="pocetak") Start new game
    div(class="polje")
      div.malaPolja(@click="promijeniPolje(rbr)" v-for="(ix_ili_ox,rbr) in polja" :key="rbr" :class="{'ix':ix_ili_ox === 'x','ox': ix_ili_ox ==='o'}")
        | {{ ix_ili_ox }}
</template>
<script>
export default {
  name: 'HelloWorld',
  data: () => ({
    activePlayer: 0,
    polja: ['1', '2', '3', '4', '5', '6', '7', '8', '9']
  }),
  methods: {
    pocetak () {
      this.activePlayer = 1
    },
    promijeniPolje (rbr) {
      console.log(this.activePlayer + '   ->   ' + rbr)
      if (this.activePlayer === 1) {
        this.polja[rbr] = 'x'
        this.activePlayer = 2
      } else if (this.activePlayer === 2) {
        this.polja[rbr] = 'o'
        this.activePlayer = 1
      }
      console.log(this.polja)
    }
  }
}
</script>

<style lang="stylus">

.polje
  padding 5px
  margin-top 60px
  width 300px
  height 300px
  margin auto
  border 25px solid green
  display flex
  flex-wrap wrap
  justify-content space-evenly
  align-items center
  align-content space-around
  flex-direction row

.startButton
  padding 10px
  margin 10px

.malaPolja
  box-sizing border-box
  width 94px
  height 94px
  font-size 90px
  padding 1px
  margin 1px
  border 1px solid blue
</style>
