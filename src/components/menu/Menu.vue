<style scoped src="./Menu.css"></style>
<template>
  <div>
    <nav class="menu-desktop">
      <div class="menu-left">
        <h1 class="logo">FHIR-Q</h1>
        <a href="#">Option 1</a>
        <a href="#">Option 2</a>
        <a href="#">Option 3</a>
      </div>
      <div class="menu-right">
        <a href="#">Other 1</a>
        <a href="#">Other 2</a>
        <a href="#">Other 3</a>
        <a href="#" v-on:click="decreaseNumber">Decrease this {{count}}</a>
      </div>
    </nav>

    <nav class="menu-mobile">
      <div class="menu-burger">
        <a class="burger-button"
           v-on:click="showMenu()">
          <i class="material-icons" style="font-size:36px;">
            dehaze
          </i>
        </a>
      </div>
      <div ref="slideMenu" class="slide-menu">
        <div class="container">
          <ul>
            <li>Hello</li>
            <li>Yellow</li>
          </ul>
        </div>
      </div>
    </nav>
  </div>
</template>
<script>
import {mapState} from "vuex";

export default {
  name: 'Menu',
  computed: mapState([
    'count'
  ]),
  data: () => {
    return {
      isShow: false
    }
  },
  mounted: function () {
    this.showMenu()
  },
  methods: {
    showMenu() {
      if (this.isShow) this.$refs.slideMenu.classList.add("slide-menu-show")
      else this.$refs.slideMenu.classList.remove("slide-menu-show")
      this.isShow = !this.isShow;
    },
    decreaseNumber(){
      this.$store.commit('decrement')
    }
  }
}
</script>