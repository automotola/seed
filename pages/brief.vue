<template lang="pug">
v-card.hide-overflow(height='200px', flat='')
  .headline.text-xs-center.pa-5
    | Active: {{ bottomNav }}
    v-card-text.text-xs-center
      v-btn(flat='', color='primary', @click='showNav = !showNav')
        | Toggle Nav
  v-bottom-nav(:active.sync='bottomNav', :value='showNav', absolute='', color='transparent')
    v-btn(color='teal', flat='', value='resources')
      span Resources
      v-icon toc
    v-btn(color='teal', flat='', value='operations')
      span Operations
      v-icon cached
    v-btn(color='teal', flat='', value='insights')
      span Information
      v-icon info_outline
</template>
<script>
export default {
  data () {
    return {
      activeBtn: 1,
      bottomNav: 'resources',
      showNav: true
    }
  }
}
</script>
