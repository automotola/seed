<template lang="pug">
v-card(flat='')
  v-container(fluid='')
    v-layout(row='', child-flex='', wrap='')
      div
        div
          v-breadcrumbs(:items='items', divider='>')
        v-toolbar
          v-btn.hidden-xs-only(icon='')
            v-icon arrow_back
          v-toolbar-title Title
          v-spacer
          v-btn.hidden-xs-only(icon='')
            v-icon search
      div(style='flex-basis: 20%')
        div
          v-breadcrumbs(:items='items')
            v-icon(slot='divider') chevron_right
        v-toolbar(dark='')
          v-spacer
          v-btn(icon='')
            v-icon reply
          v-btn(icon='')
            v-icon more_vert
  v-data-table.elevation-1(v-model='selected', :headers='headers', :items='desserts', :pagination.sync='pagination', select-all='', item-key='name')
    template(slot='headers' slot-scope='props')
      tr
        th
          v-checkbox(:input-value='props.all' :indeterminate='props.indeterminate' primary='' hide-details='' @click='toggleAll')
        th(v-for='header in props.headers' :key='header.text' :class="['column sortable', pagination.descending ? 'desc' : 'asc', header.value === pagination.sortBy ? 'active' : '']" @click='changeSort(header.value)')
          v-icon(small='') arrow_upward
          |           {{ header.text }}
    template(slot='items' slot-scope='props')
      tr(:active='props.selected' @click='props.selected = !props.selected')
        td
          v-checkbox(:input-value='props.selected' primary='' hide-details='')
        td {{ props.item.name }}
        td.text-xs-right {{ props.item.calories }}
        td.text-xs-right {{ props.item.fat }}
        td.text-xs-right {{ props.item.carbs }}
        td.text-xs-right {{ props.item.protein }}
        td.text-xs-right {{ props.item.iron }}

</template>
<script>
  export default {
    data: function(){
      return {
        pagination: {
          sortBy: 'name'
        },
        selected: [],
        headers: [
          {
            text: 'Dessert (100g serving)',
            align: 'left',
            value: 'name'
          },
          { text: 'Calories', value: 'calories' },
          { text: 'Fat (g)', value: 'fat' },
          { text: 'Carbs (g)', value: 'carbs' },
          { text: 'Protein (g)', value: 'protein' },
          { text: 'Iron (%)', value: 'iron' }
        ],
        desserts: [
          {
            value: false,
            name: 'Frozen Yogurt',
            calories: 159,
            fat: 6.0,
            carbs: 24,
            protein: 4.0,
            iron: '1%'
          },
          {
            value: false,
            name: 'Ice cream sandwich',
            calories: 237,
            fat: 9.0,
            carbs: 37,
            protein: 4.3,
            iron: '1%'
          },
          {
            value: false,
            name: 'Eclair',
            calories: 262,
            fat: 16.0,
            carbs: 23,
            protein: 6.0,
            iron: '7%'
          },
          {
            value: false,
            name: 'Cupcake',
            calories: 305,
            fat: 3.7,
            carbs: 67,
            protein: 4.3,
            iron: '8%'
          },
          {
            value: false,
            name: 'Gingerbread',
            calories: 356,
            fat: 16.0,
            carbs: 49,
            protein: 3.9,
            iron: '16%'
          },
          {
            value: false,
            name: 'Jelly bean',
            calories: 375,
            fat: 0.0,
            carbs: 94,
            protein: 0.0,
            iron: '0%'
          },
          {
            value: false,
            name: 'Lollipop',
            calories: 392,
            fat: 0.2,
            carbs: 98,
            protein: 0,
            iron: '2%'
          },
          {
            value: false,
            name: 'Honeycomb',
            calories: 408,
            fat: 3.2,
            carbs: 87,
            protein: 6.5,
            iron: '45%'
          },
          {
            value: false,
            name: 'Donut',
            calories: 452,
            fat: 25.0,
            carbs: 51,
            protein: 4.9,
            iron: '22%'
          },
          {
            value: false,
            name: 'KitKat',
            calories: 518,
            fat: 26.0,
            carbs: 65,
            protein: 7,
            iron: '6%'
          }
        ],
        items: [
          {
            text: 'Dashboard',
            disabled: false,
            href: 'breadcrumbs_dashboard'
          },
          {
            text: 'Link 1',
            disabled: false,
            href: 'breadcrumbs_link_1'
          },
          {
            text: 'Link 2',
            disabled: true,
            href: 'breadcrumbs_link_2'
          }
        ]
      }
    },
    methods: {
      toggleAll () {
        if (this.selected.length) this.selected = []
        else this.selected = this.desserts.slice()
      },
      changeSort (column) {
        if (this.pagination.sortBy === column) {
          this.pagination.descending = !this.pagination.descending
        } else {
          this.pagination.sortBy = column
          this.pagination.descending = false
        }
      }
    }
  }
</script>