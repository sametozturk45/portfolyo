<template>
    <div class="pa-4">
        <ContactCard />
    </div>
</template>

<script>
    export default {
        name:'BanaUlasin',
        head(){
            return{
            title:'Bana Ulaşın'
            }
        },
        created() {
            this.$nuxt.$emit('transparent-appbar', false)
            this.$nuxt.$emit('fixed-appbar', false)
        },
        components:{
            ContactCard:()=>import('~/components/static/ContactCard')
        },
    }
</script>