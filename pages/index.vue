<template>
  <div>
    <div class="position-relative overflow-hidden">
      <v-img id="bulut1" class="parallax-item" src="/bulut1.png" width="620px" contain eager />
      <v-img id="bulut2" class="parallax-item" src="/bulut2.png" width="200px" contain eager />
      <v-img id="bulut3" class="parallax-item" src="/bulut3.png" width="450px" contain eager />
      <div id="parallax-text-wrapper" class="parallax-item">
        <div id="parallax-text-container" class="mx-auto">
          <v-img id="profil-fotografi" src="/samet-ozturk.jpg" height="128" width="128" :aspect-ratio="1"
            position="center center" />
          <h1 class="white--text"><span id="parallax-text-header">SAMET ÖZTÜRK</span><span id="carrot">|</span></h1>
          <h2 class="white--text" id="parallax-text-desc">Yazılım Geliştiricisi</h2>
          <v-btn color="secondary" href="/SametOZTURK.pdf" class="mt-4" rounded download><v-icon
              class="mr-2">mdi-file</v-icon>Download CV</v-btn>
        </div>
      </div>
      <v-img id="parallax-background" src="/background.jpg" width="100%" max-height="50rem" :aspect-ratio="1 / 2" eager />
    </div>
    <div class="pa-4 pb-14">
      <v-card width="100%">
        <v-card-title>Merhaba,</v-card-title>
        <v-card-text>
          Ben Samet ÖZTÜRK, 22 yaşında bir yazılım geliştiricisiyim. <span class="secondary--text font-weight-bold">Algoritma kurmayı ve çözmeyi</span> seven biriyimdir. “Bu sorunu nasıl <span class="secondary--text font-weight-bold">kalıcı olarak çözebilir</span> ve bulduğum çözümü en
          iyi biçimde nasıl anlatabilirim.” diye hep düşünür ve çözümlerimin bir o kadar <span class="secondary--text font-weight-bold">anlaşılır ve temiz olmasına özen
          gösteririm.</span> Kendi düşünce tarzımı açıklamayı ve farklı fikirleri de toplayıp kendi düşüncemi geliştirebilecek
          olan fikirleri derleyip çıkardığım ürünlerin <span class="secondary--text font-weight-bold">daha sürdürülebilir</span> olmasını sağlıyorum. <span class="secondary--text font-weight-bold">Takım canlısı</span> ve güleç bir
          kişiliğe sahibim. Hedefim <span class="secondary--text font-weight-bold">sektörün zirvesine</span> ulaşıp daha da gelişmek.
        </v-card-text>
      </v-card>
      <v-card class="mt-4" width="100%" v-if="getProjeler.length > 0">
        <v-card-title class="justify-space-between">
          Projelerim
          <v-btn color="secondary" to="/projelerim/listele" text>
            HEPSİNİ GÖR
          </v-btn>
        </v-card-title>
        <v-card-text>
          <v-row cols="12">
            <v-col class="col-12 col-md-6 col-lg-4" v-for="(item, index) in getProjeler" :key="index">
              <v-card color="accent" class="mx-auto project-card" width="100%">
                <v-img :src="item?.img" height="18rem" />
                <v-card-title>
                  <nuxt-link class="text-decoration-none white--text" :to="`/projelerim/listele/${item?.id}`">{{
                    item?.title }}</nuxt-link>
                </v-card-title>

                <v-card-text>
                  {{ item?.desc }}
                </v-card-text>
                <v-divider dark />
                <v-card-actions class="overflow-x-auto role-badges">
                  <v-chip class="mx-1 d-table" :color="rol?.color" v-for="(rol, index) in getProjeRolleri(item)"
                    :key="index" outlined small>
                    {{ rol?.title }}
                  </v-chip>
                </v-card-actions>
              </v-card>
            </v-col>
          </v-row>
        </v-card-text>
      </v-card>
      <h2 class="text-center my-12 text-h2">Bana Ulaşın</h2>
      <ContactCard />
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  head(){
    return{
      title:'Anasayfa'
    }
  },
  created() {
    this.$nuxt.$emit('transparent-appbar', true)
    this.$nuxt.$emit('fixed-appbar', true)
  },
  data() {
    return {
      isValid: false
    }
  },
  computed: {
    getProjeler() {
      return this.$store.state.projeler.items
    },
    getRoller() {
      return this.$store.state.enums.roller.items
    }
  },
  methods: {
    parallaxEffect() {
      const targetHeight = 45 * parseFloat(getComputedStyle(document.documentElement).fontSize)
      let bulut1 = document.getElementById('bulut1')
      let bulut2 = document.getElementById('bulut2')
      let bulut3 = document.getElementById('bulut3')
      let parallaxText = document.getElementById('parallax-text-wrapper')

      if (window.scrollY > targetHeight)
        this.$nuxt.$emit('transparent-appbar', false)
      else
        this.$nuxt.$emit('transparent-appbar', true)

      bulut1.style.transform = `translateX(${window.scrollY / 1.2}px)`
      bulut2.style.transform = `translateX(${window.scrollY / 1.2}px)`
      bulut3.style.transform = `translateX(${window.scrollY / 1.2}px)`
      parallaxText.style.transform = `translateY(${window.scrollY * 0.7}px)`
    },
    getProjeRolleri(item) {
      return this.getRoller.filter(x => item?.roller?.includes(x.id))
    }
  },
  components: {
    ContactCard: () => import('~/components/static/ContactCard')
  },
  beforeMount() {
    window.addEventListener('scroll', this.parallaxEffect)
  },
  beforeDestroy() {
    window.removeEventListener('scroll', this.parallaxEffect)
  }
}
</script>

<style scoped>
@media (min-width:420) {
  .letter-spacing-button {
    letter-spacing: 0.0892857143em;
  }
}

.parallax-item {
  position: absolute;
  z-index: 3
}

#profil-fotografi {
  position: absolute;
  border-radius: 50%;
  transform: translateY(-9rem) translateX(3rem);
}

#parallax-background {
  z-index: 1
}

#parallax-text-wrapper {
  top: 18rem;
  left: 0;
  right: 0;
}

#parallax-text-container {
  width: fit-content;
  background: #594CB657;
  padding: 5rem 5rem 3rem 5rem;
  text-align: center;
  border-radius: 16px;
  backdrop-filter: blur(6px);
}

#bulut1 {
  top: 0;
  left: -500px;
}

#bulut2 {
  top: 130px;
  left: 80px;
}

#bulut3 {
  top: 120px;
  right: -150px;
}

#parallax-text-header {
  display: inline-flex;
  font-family: monospace;
  text-wrap: nowrap;
  overflow-x: hidden;
  animation: writeHeader 6s steps(12) infinite;
}

@keyframes writeHeader {
  0% {
    width: 0ch;
  }

  50% {
    width: 12ch;
  }
}

#carrot {
  animation: carrotBlink 1s infinite;
}

@keyframes carrotBlink {

  0%,
  100% {
    opacity: 100%
  }

  50% {
    opacity: 0%;
  }
}

.position-relative {
  position: relative;
}

.project-card {
  transition: 0.5s;
}

.project-card:hover {
  transition: 0.4s;
  transform: translateY(-0.5rem);
}

.role-badges::-webkit-scrollbar {
  display: none;
}

.role-badges {
  -ms-overflow-style: none;
  scrollbar-width: none;
}</style>