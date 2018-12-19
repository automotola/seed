<template lang="pug">
  v-container(fluid='', grid-list-lg='')
    v-layout(row='', wrap='')
      v-flex(xs12='', sm12='', md6='')
        v-card
          v-toolbar
            v-toolbar-side-icon
          v-card-text.grey.lighten-5(style='height: 300px;')
          v-card-text(style='height: 100px; position: relative')
            v-btn(absolute='', dark='', fab='', top='', right='', color='pink')
              v-icon add
      v-flex(xs12='', sm12='', md6='')
        v-card
          v-toolbar(extended='')
            v-toolbar-side-icon
            v-fab-transition
              v-btn(v-show='!hidden', color='pink', fab='', dark='', small='', absolute='', bottom='', left='')
                v-icon add
          v-card-text.grey.lighten-5.text-xs-center(style='height: 300px;')
            v-btn(color='primary', @click='hidden = !hidden')
              | {{ hidden ? 'Show' : 'Hide' }}
          v-card-text(style='height: 100px; position: relative')
            v-fab-transition
              v-btn(v-show='!hidden', color='pink', dark='', absolute='', top='', right='', fab='')
                v-icon add
</template>
<script>
  export default {
    data: () => ({
      hidden: false
    })
  }
</script>