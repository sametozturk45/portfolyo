<template>
  <v-app dark>
    <Appbar :class="{'transparent-background':isTransparent,'accent':!isTransparent}" :fixed="fixedAppbar" @openDrawer="drawer = true" />
    <v-navigation-drawer
            v-model="drawer"
            id="drawer"
            fixed
            :color="!$vuetify.theme.isDark ?'secondary':''"
            >
            <v-list class="pa-4" rounded dark>
                <h2 class="text-button"><nuxt-link class="text-decoration-none white--text" to="/">SAMET ÖZTÜRK</nuxt-link></h2>
                <v-divider class="mb-2" dark />
                <v-list-item to="/projelerim/listele" exact-path>Projelerim</v-list-item>
                <v-list-item to="/banaUlasin" exact-path>Bana Ulaşın</v-list-item>
            </v-list>
            </v-navigation-drawer>
    <main>
      <v-layout>
        <v-container class="pa-0 ma-0" fluid>
          <Nuxt />
        </v-container>
      </v-layout>
    </main>
    <v-overlay :opacity="0.8" :value="loading" id="overlay">
        <v-img :class="loaderClasses" :src="`/loaders/${loaderImageNumber}.gif`" width="300" height="auto" :aspect-ratio="1/2" contain/>
    </v-overlay>
    <v-footer color="accent" app>
      <span class="white--text">&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: 'DefaultLayout',
  created(){
    this.$nuxt.$on('transparent-appbar',(value)=>this.isTransparent = value)
    this.$nuxt.$on('fixed-appbar',(value)=>this.fixedAppbar = value)
    this.$nuxt.$on('loading',(value)=>{
      this.loaderImageNumber = (Math.floor(Math.random()*15)+1)
      this.loading = value
    })
  },
  data() {
    return {
      title: 'Samet ÖZTÜRK',
      loaderImageNumber:1,
      drawer:false,
      isTransparent:false,
      fixedAppbar:false,
      loading:false
    }
  },
  computed:{
    loaderClasses(){
      if([2,3,11].includes(parseInt(this.loaderImageNumber)))
        return 'animated-loader-gif'
      else
        return ''
    }
  },
  components: {
    Appbar: () => import('~/components/static/Appbar')
  }
}
</script>

<style>
html {
  overflow-y: auto;
  scroll-behavior: smooth !important;
}

html::-webkit-scrollbar-track{
  -webkit-box-shadow: inset 0 0 6px #5d5d5d !important;
  background-color: #5d5d5d !important;
}

html::-webkit-scrollbar{
  width: 0px !important;
}

html::-webkit-scrollbar-thumb{
  -webkit-box-shadow: inset 0 0 6px #424242 !important;
  background-color: #424242 !important;
}

.transparent-background{
  background-color: #22222256 !important;
}

.theme--light.v-application{
  background:#2A264F !important;
}

.theme--light.v-card{
  background:#302D72 !important;
}


.theme--light.v-card,
.theme--light ::selection,
.theme--light.v-application{
  color:#fafafa !important;
}

.theme--light.v-card > .v-card__subtitle,
.theme--light.v-card > .v-card__text{
  color:rgba(255,255,255,0.7) !important;
}

.theme--light ::selection{
  background:#9476CA !important;
}

#overlay{
  z-index:90 !important;
}

.animated-loader-gif{
  animation: loader 3s infinite ease-in-out;
}

@keyframes loader{
  to{
    transform:translateX(100%)
  }
  from{
    transform:translateX(-100%)
  }
}

#drawer{
  z-index:130 !important
}
</style>
