<template>
  <div class="home">
    <div v-show="loading" style="text-align: center;"> <h1> <i>Loading ...</i> </h1></div>
    <div id="poll" v-if="polls.length > 0">
      <PollTile v-for="poll in polls" :key="poll._id" :poll="poll"/>
    </div>
    <div v-else style="text-align: center;"><h2>No Poll</h2></div>
  </div>
</template>

<script>
// @ is an alias to /src
import PollTile from '@/components/PollTile.vue'
import axios from 'axios'

export default {
  name: 'home',
  data () {
    return {
      loading: true,
      polls: []
    }
  },
  components: {
    PollTile
  },
  computed: {
    /* polls () {
      return this.$store.state.polls
    } */
  },
  mounted () {
    axios.get('http://localhost:3000/api/polls')
      .then((res) => {
        this.loading = false
        this.polls = res.data
      })
  }
}
</script>

<style scoped>
</style>
