<template>
    <div class="d-flex px-4 py-6" :class="{'fixed-appbar':fixed}" v-bind="$attrs">
        <v-btn @click="$emit('openDrawer',true)" class="mr-2 d-sm-none" color="white" icon><v-icon>mdi-menu</v-icon></v-btn>
        <nuxt-link to="/" class="text-decoration-none text-button white--text" text>SAMET ÖZTÜRK</nuxt-link>
        <v-spacer />
        <nuxt-link exactActiveClass="menu-link--active" to="/projelerim/listele" class="text-decoration-none text-button white--text px-4 mr-2 d-none d-sm-inline menu-link">Projelerim</nuxt-link>
        <nuxt-link exactActiveClass="menu-link--active" to="/banaUlasin" class="text-decoration-none text-button white--text px-4 mr-2 d-none d-sm-inline menu-link">Bana Ulaşın</nuxt-link>
        <v-btn class="white--text" @click="toggleThemeSwitcher" icon><v-icon>{{ $vuetify.theme.isDark ? 'mdi-white-balance-sunny' : 'mdi-weather-night' }}</v-icon></v-btn>
    </div>
</template>

<script>
    export default {
        name:'Appbar',
        methods:{
            toggleThemeSwitcher(){
                this.$vuetify.theme.dark = !this.$vuetify.theme.dark
            }
        },
        props:{
            fixed:{
                type:Boolean,
                default:false
            }
        }
    }
</script>

<style scoped>
    .fixed-appbar{
        position: fixed;
        top:0;
        right:0;
        left:0;
        z-index: 50;
    }
    .menu-link:hover{
        background-color:#fafafa;
        color:#222 !important;
        border-radius:16px;
    }

    .menu-link--active{
        background-color:#fafafa;
        color:#222 !important;
        border-radius:16px;
    }
</style>