<template lang="pug">
.root
  #lateral
    v-toolbar(dark='', tabs='', flat='', color='indigo')
      v-toolbar-side-icon
      v-toolbar-title Page title
      v-spacer
      v-btn(icon='')
        v-icon search
      v-btn(icon='')
        v-icon more_vert
      v-tabs(slot='extension', v-model='tabs', align-with-title='', color='transparent')
        v-tab(href='#one') Item One
        v-tab(href='#two') Item Two
        v-tab(href='#three') Item Three
        v-tabs-slider(color='pink')
    v-tabs-items(v-model='tabs')
      v-tab-item(v-for="content in ['one', 'two', 'three']", :key='content', :id='content')
        v-card(height='200px', flat='')
      v-fab-transition
        v-bottom-sheet(v-model='sheet')
          v-btn(:color='activeFab.color', :key='activeFab.icon', v-model='fab', dark='', fab='', fixed='', bottom='', right='', open-on-hover='', slot='activator')
            v-icon {{ activeFab.icon }}
            v-icon close
          v-list
              v-subheader Open in
              v-list-tile(v-for='tile in tiles', :key='tile.title', @click='sheet = false')
                v-list-tile-avatar
                  v-avatar(size='32px', tile='')
                    img(:src='`https://cdn.vuetifyjs.com/images/bottom-sheets/${tile.img}`', :alt='tile.title')
                v-list-tile-title {{ tile.title }}

</template>
<script>
  export default {
    data: () => ({
      sheet: false,
      fab: false,
      hidden: false,
      tabs: null,
      tiles: [
        { img: 'keep.png', title: 'Keep' },
        { img: 'inbox.png', title: 'Inbox' },
        { img: 'hangouts.png', title: 'Hangouts' },
        { img: 'messenger.png', title: 'Messenger' },
        { img: 'google.png', title: 'Google+' }
      ]
    }),
    computed: {
      activeFab () {
        switch (this.tabs) {
          case 'one': return { 'color': 'indigo', icon: 'share' }
          case 'two': return { 'color': 'red', icon: 'edit' }
          case 'three': return { 'color': 'green', icon: 'keyboard_arrow_up' }
          default: return {}
        }
      }
    }
  }
</script>