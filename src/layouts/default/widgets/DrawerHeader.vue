<template>
  <v-list-item
    class="mb-0 justify-space-between pl-3 flex flex-column"
    active-class="white--text"
    to="/"
    :ripple="false"
  >
    <v-list-item-avatar
      style="width: 85%; min-width: 80%; height: auto; margin: 20px 0"
    >
      <v-img
        :src="logoImage"
      />
    </v-list-item-avatar>

    <v-list-item-content class="pl-2">
      <v-list-item-title class="text-h3">
        Tarkov Tracker
        <div v-if="$firebase.options.projectId != 'tarkovtracker-59ebc'">
          DEVELOPMENT
        </div>
      </v-list-item-title>
    </v-list-item-content>
  </v-list-item>
</template>

<script>
  // Utilities
  import { sync } from 'vuex-pathify'

  export default {
    name: 'DefaultDrawerHeader',

    computed: {
      logoImage () {
        // If we're not on official tarkovtracker environment, show dev logo
        if (this.$firebase.options.projectId != "tarkovtracker-59ebc") {
          return '/img/tarkovtrackerlogo-development.png'
        }

        if (this.mini) {
          return '/img/tarkovtrackerlogo-mini.png'
        } else {
          return '/img/tarkovtrackerlogo-light.png'
        }
      },

      ...sync('app', [
        'mini',
      ]),
    },
  }
</script>
