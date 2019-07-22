<template>
  <v-toolbar
    id="core-toolbar"
    fixed
    style="background: #eee;"
  >
   <v-spacer></v-spacer>
    <v-toolbar-items>
      <v-flex
        align-center
        layout
        py-2
      > 
      <h6 style="margin-right:100px;">Time Left
        <p>24:60:60</p>
      </h6>
      <v-avatar color="grey lighten-4">
         <v-icon color="tertiary" >mdi-account</v-icon>
      </v-avatar>
          <h6 style="padding-left:15px;">Moderator</h6>
      </v-flex>
    </v-toolbar-items>
  </v-toolbar>
</template>

<script>

import {
  mapMutations
} from 'vuex'

export default {
  data: () => ({
    title: null,
    responsive: false,
    responsiveInput: false
  }),

  watch: {
    '$route' (val) {
      this.title = val.name
    }
  },

  mounted () {
    this.onResponsiveInverted()
    window.addEventListener('resize', this.onResponsiveInverted)
  },
  beforeDestroy () {
    window.removeEventListener('resize', this.onResponsiveInverted)
  },

  methods: {
    ...mapMutations('app', ['setDrawer', 'toggleDrawer']),
    onClickBtn () {
      this.setDrawer(!this.$store.state.app.drawer)
    },
    onClick () {
      //
    },
    onResponsiveInverted () {
      if (window.innerWidth < 991) {
        this.responsive = true
        this.responsiveInput = false
      } else {
        this.responsive = false
        this.responsiveInput = true
      }
    }
  }
}
</script>

<style>
  #core-toolbar a {
    text-decoration: none;
  }
</style>
