<template>
  <v-app  :class="{ ltrFont: !$vuetify.rtl }">
     <Header />
    <MainView />

  </v-app>
</template>

<script>
import MainView from './defaultSections/mainView'
import Header from './defaultSections/header'

export default {
  components: {
    MainView,
    Header,
  },
  data() {
    return {
      fetchDoneFlag: false
    }
  },
}
</script>
