<template>
  <v-app dark>
    <v-navigation-drawer
      :mini-variant="miniVariant"
      :clipped="clipped"
      :right="rightMap"
      v-model="drawer"
      fixed
      floating
      app
    >
      <v-toolbar 
        flat 
        class="transparent">
        <v-list class="pa-0">
          <v-list-tile avatar>
            <v-list-tile-avatar>
              <img src="https://randomuser.me/api/portraits/men/85.jpg">
            </v-list-tile-avatar>

            <v-list-tile-content>
              <v-list-tile-title>John Leider</v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
        </v-list>
      </v-toolbar>
      <v-list>
        <v-list-tile
          v-for="(item, i) in items"
          :to="item.to"
          :key="i"
          router
          exact
        >
          <v-list-tile-action>
            <v-icon v-html="item.icon" />
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title v-text="item.title" />
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar
      :clipped-left="clipped"
      fixed
      app
    >
      <v-btn
        icon
        @click.stop="drawer = !drawer"
      >
        <v-icon>dialpad</v-icon>
      </v-btn>
      <v-toolbar-title v-text="title"/>
      <v-spacer/>
      <v-btn
        icon
        @click.stop="clipped = !clipped"
      >
        <v-icon>web</v-icon>
      </v-btn>
      <v-btn
        icon
        @click.stop="fixed = !fixed"
      >
        <v-icon>remove</v-icon>
      </v-btn>

      <v-btn
        icon
        @click.stop="rightDrawer = !rightDrawer"
      >
        <v-icon>fingerprint</v-icon>
      </v-btn>
    </v-toolbar>
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
    <v-navigation-drawer
      :right="rightPath"
      v-model="rightDrawer"
      temporary
      fixed
    >
      <v-list>
        <v-list-tile @click.native="right = !right">
          <v-list-tile-action>
            <v-icon light>compare_arrows</v-icon>
          </v-list-tile-action>
          <v-list-tile-title>Switch drawer (click me)</v-list-tile-title>
        </v-list-tile>
      </v-list>
      <v-timeline>
        <v-timeline-item
          v-for="n in 4"
          :key="n"
          color="red lighten-2"
          large
        >
          <span slot="opposite">Tus eu perfecto</span>
          <v-card class="elevation-2">
            <v-card-title class="headline">Lorem ipsum</v-card-title>
            <v-card-text>
              Lorem ipsum dolor sit amet, no nam oblique veritus. Commune scaevola imperdiet nec ut, sed euismod convenire principes at. Est et nobis iisque percipit, an vim zril disputando voluptatibus, vix an salutandi sententiae.
            </v-card-text>
          </v-card>
        </v-timeline-item>
      </v-timeline>
    </v-navigation-drawer>
  </v-app>
</template>

<script>
  export default {
    data() {
      return {
        clipped: false,
        drawer: false,
        fixed: false,
        items: [
          { icon: 'code', title: 'Work', to: '/' },
          { icon: 'book', title: 'Acknowledge', to: '/brief' },
          { icon: 'timeline', title: 'Narrate', to: '/content' },
          { icon: 'change_history', title: 'Develop', to: '/document' }
        ],
        miniVariant: false,
        rightPath: false,
        rightMap: true,
        rightDrawer: false,
        title: 'Mark™'
      }
    }
  }
</script>
