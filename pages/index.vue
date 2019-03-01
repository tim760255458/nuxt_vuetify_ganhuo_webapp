<template>
  <v-layout
    column
    justify-center
    align-center
  >
    <template v-for="item of tags">
      <v-card
        :key="item"
        ripple
        xs12
        sm8
        md6
        class="v-card-margin v-card-width"
      >
        <v-card-title class="headline">
          {{ item }}
        </v-card-title>
        <v-card-text>
          {{ item }}
        </v-card-text>
        <v-card-actions>
          <v-spacer />
          <v-btn
            color="primary"
            nuxt
            small
            to="/inspire"
          >
            进入
          </v-btn>
        </v-card-actions>
      </v-card>
    </template>
  </v-layout>
</template>

<script>
import axios from 'axios'

export default {
  components: {},
  data() {
    return {
      tags: [],
      todayData: {}
    }
  },
  created() {
    this.queryToday()
  },
  methods: {
    queryToday() {
      axios.get('/api/today').then(
        res => {
          console.log(res)
          this.tags = res.data.category
          this.todayData = res.data.results
        },
        err => {
          console.log(err)
        }
      )
    }
  }
}
</script>
