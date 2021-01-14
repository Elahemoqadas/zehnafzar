<template>
  <v-app-bar
  flat
    id="appHeader"
    app
    color="grey lighten-3"
    :extended="$vuetify.breakpoint.smAndUp"
    :dense="$vuetify.breakpoint.xsOnly"
  >
    <v-app-bar-nav-icon
      color="color11"
    >
    </v-app-bar-nav-icon>


    <v-spacer></v-spacer>

    <div>
            <v-btn color="color6" icon >
              <v-badge
                :content="messages"
                :value="messages"
                color="red"
                overlap
              >
                <v-icon>mdi-bell-outline</v-icon>
              </v-badge>
            </v-btn>
    </div>
      <div>
         <img
        src="/v.png"
          width="48"
          class="rounded-pill elevation-3 mr-8"
      >
      </div>
  </v-app-bar>
</template>

<script>
export default {
  data() {
    return {
      messages: 2
    }
  }
}
</script>
