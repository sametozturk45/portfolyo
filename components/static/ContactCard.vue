<template>
    <v-card class="pa-8 mx-auto">
        <v-row cols="12">
          <v-col class="col-12 col-md-6 col-lg-4 text-center text-md-start">
            <h2 class="mt-2">Samet ÖZTÜRK</h2>
            <h4 class="mt-2"><v-icon color="white" class="mr-3">mdi-mail</v-icon><a target="_blank"
                class="white--text text-decoration-none"
                href="mailto:sametozturk.info@gmail.com">sametozturk.info@gmail.com</a></h4>
            <h4 class="mt-2"><v-icon color="white" class="mr-3">mdi-phone</v-icon><a target="_blank"
                class="white--text text-decoration-none" href="tel:+905324770194">+90 532 477 01 94</a></h4>
          </v-col>
          <v-col class="col-12 col-md-6 col-lg-8 d-flex flex-column align-center align-md-end justify-center">
            <v-divider width="100%" class="d-md-none" dark/>
            <h2 class="letter-spacing-button mt-4">FRONT END DEV<span class="d-none d-sm-inline">ELOPER</span></h2>
          </v-col>
        </v-row>
      </v-card>
</template>

<script>
    export default {
        name:'ContactCard'
    }
</script>