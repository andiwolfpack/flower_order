<template>
  <v-app>
    <v-toolbar app>
      <v-toolbar-title class="headline text-uppercase">
        <span class="font-weight-light">Flower orders</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn @click="showComponent">
        <span class="mr-2">{{showMessage}}</span>
      </v-btn>
    </v-toolbar>

    <v-content>
      <HelloWorld v-show="show"></HelloWorld>
    </v-content>
  </v-app>
</template>

<script>
  import HelloWorld from './components/HelloWorld'
  import Andi from './components/andi.vue'

  export default {
    name: 'App',

    components: {
      HelloWorld
    },

    data() {
      return {
        show: true,
        showMessage: 'Hide list'
      }
    },

    methods: {
      showComponent() {
        if (this.show) {
          this.show = false
          this.showMessage = 'Show list'
        } else {
          this.show = true
          this.showMessage = 'Hide list'
        }
      }
    }
  }
</script>