<template lang="pug">
v-app(dark='')
  v-navigation-drawer(:mini-variant='miniVariant' :clipped='clipped' v-model='drawer' fixed='' floating='' app='')
    v-list.pax-2
      v-list-tile(v-for='(item, i) in items' :to='item.to' :key='i' router='' exact='')
        v-list-tile-action
          v-icon(v-html='item.icon')
        v-list-tile-content
          v-list-tile-title(v-text='item.title')
      v-divider
        v-list-tile(@click.stop='miniVariant= !miniVariant')
          v-list-tile-action
            v-icon(v-html="'visibility'")
          v-list-tile-content
            v-list-tile-title(v-text="'Collapse'")
  v-toolbar(fixed='' app='')
    v-btn(icon='' @click.stop='drawer = !drawer')
      v-icon dialpad
    v-toolbar-title(v-text='title')
      v-spacer
        v-btn(icon='' @click.stop='fixed = !fixed')
          v-icon remove
        v-btn(icon='' @click.stop='rightDrawer = !rightDrawer')
          v-icon fingerprint
  v-content
    v-container
      nuxt
  v-navigation-drawer(:right='right' v-model='rightDrawer' :clipped='rightClipped' fixed='' temporary='')
    v-list
      v-list-tile.pay-0(avatar='')
        v-list-tile-avatar
          img(:src='avatar.persona[0].img')
        v-list-tile-content
          v-list-tile-title Mark One
      v-divider
        v-list-tile(@click.native='right = !right')
          v-list-tile-action
            v-icon(light='') compare_arrows
          v-list-tile-title Switch drawer (click me)
    v-timeline
      v-timeline-item(v-for='n in 4' :key='n' color='red lighten-2' large='')
        span(slot='opposite') Tus eu perfecto
        v-card.elevation-2
          v-card-title.headline Lorem ipsum
          v-card-text
            | Lorem ipsum dolor sit amet, no nam oblique veritus. Commune scaevola imperdiet nec ut, sed euismod convenire principes at. Est et nobis iisque percipit, an vim zril disputando voluptatibus, vix an salutandi sententiae.
</template>


<script>
  export default {
    data() {
      return {
        items: [
          { icon: 'category', title: 'Work', to: '/' },
          { icon: 'book', title: 'Acknowledge', to: '/brief' },
          { icon: 'timeline', title: 'Narrate', to: '/content' },
          { icon: 'code', title: 'Design', to: '/document' },
          { icon: 'touch_app', title: 'Apply', to: '/experience'}
        ],
        avatar: {
          persona: [
            {img: 'https://scontent-amt2-1.cdninstagram.com/vp/a446659746a81bc7fd51f8c2d3f61a99/5C934F7D/t51.2885-19/s150x150/43025534_340578996690957_5974282625219559424_n.jpg?_nc_ht=scontent-amt2-1.cdninstagram.com'},
            {img: 'https://scontent-amt2-1.cdninstagram.com/vp/db3b8d923fd625887a45f2bdb4e805d7/5CAB7C98/t51.2885-19/s150x150/41046488_1002064639954194_8307710534338215936_n.jpg?_nc_ht=scontent-amt2-1.cdninstagram.com'}
          ]
        },
        miniVariant: false,
        clipped: false,
        drawer: true,
        right: true,
        rightClipped: true,
        rightDrawer: true,
        title: 'Mark™'
      }
    }
  }
</script>
