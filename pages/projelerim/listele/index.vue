<template>
    <div class="pa-4 pb-14">
        <v-row cols="12" v-if="getProjeler.length > 0">
            <v-col class="col-12 col-md-6 col-lg-4" v-for="(item, index) in getProjeler" :key="index">
                <v-card color="accent" class="mx-auto project-card" width="100%">
                    <v-img :src="item?.img" height="18rem"/>
                    <v-card-title>
                        <nuxt-link class="text-decoration-none white--text" :to="`/projelerim/listele/${item?.id}`">{{ item?.title }}</nuxt-link>
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
        <h2 class="mt-4 text-subtitle-1 text-center" v-else>Maalesef, gösterilecek proje yok. En yakın zamanda eklemeleri yapacağım...</h2>
    </div>
</template>

<script>
export default {
    name: 'Projelerim',
    head(){
    return{
      title:'Projelerim'
    }
  },
    created() {
        this.$nuxt.$emit('transparent-appbar', false)
        this.$nuxt.$emit('fixed-appbar', false)
    },
    computed: {
        getProjeler() {
            return this.$store.state.projeler.items
        },
        getRoller() {
            return this.$store.state.enums.roller.items
        }
    },
    methods:{
        getProjeRolleri(item){
            return this.getRoller.filter(x=>item?.roller?.includes(x.id))
        }
    }
}
</script>

<style scoped>
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
}
</style>