<template lang='pug'>
    v-content
      v-container(login-page fill-height column align-initial)
        v-layout.main-part.wrap
          v-flex(md4 sm12 order-xs2 order-md1) 
            v-form.login-page__form
              .form-group.mb-4
                input(type='text' placeholder='Email').text-input
              .form-group.mb-4
                input(type='text' placeholder='Password').text-input
              v-checkbox(label='Remember Me' outlined dark)
              v-btn(color='primary').form__submit-btn Login

          v-flex(login-page__welcome lg6 md7 sm12 offset-md1 order-xs1 order-md2 :class='{smAndDown}')
            .welcome__text
              p.subtitle-1.font-weight-regular.mb-2 Discover The Treasures
              h1.display-2.font-weight-bold.pb-2.carousel-text 
                v-carousel(vertical hide-delimiters :show-arrows='false' cycle interval='2000' continuous height='57') 
                  v-carousel-item Turkey
                  v-carousel-item North Cyprus
                    
                span Expert
              h1(v-text='$t("login.welcome.st2")').display-2.font-weight-light.mb-5
              .discover-group(:class='{smAndDown}')
                v-btn(color='primary').mr-8
                  | Discover 
                  v-icon mdi-chevron-right
                span.mt-2 The system is a nutshell
            .welcome__play.align-center.flex(v-if='!smAndDown')
              v-btn(icon color='white' height='80' width='80')
                v-icon(size='60') mdi-play

</template>

<script>
import HeaderComponent from "@/components/Header"
import FooterComponent from "@/components/Footer"

export default {
  created() {
    this.$store.commit("styles/setHeaderLogoStyle", "light")
    this.$store.commit("styles/setFooterBg", false)
    this.$store.commit("styles/setAppClassName", "login-page")
  },
  computed: {
    xs() {
      return this.$vuetify.breakpoint.xs
    },
    smAndDown() {
      return this.$vuetify.breakpoint.smAndDown
    }
  },
  components: {
    HeaderComponent,
    FooterComponent
  }
}
</script>
<style lang="sass" scoped>
@import '@/assets/styles/pages/login.sass'
@import '@/assets/styles/components/inputs.sass'
</style>
