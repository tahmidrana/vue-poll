<template>
  <div>
    <div class="card">
      <div v-show="loading" style="text-align: center;"> <h1> <i>Loading ...</i> </h1></div>
      <h2 class="poll-title">{{ poll.poll_text }}</h2>
      <p class="poll-feat">Posted on <span class="poll-date">{{ poll.created_date | formatDate }}</span> By <span class="poll-author">{{ poll.author.name }}</span></p>
      <ul class="options" v-if="poll.options.length > 0">
        <li v-for="option in poll.options" :key="option._id"><input type="radio" name="options"> {{ option.option_text }} </li>
      </ul>
      <h3 v-else>No option found for this poll :( </h3>
      <input type="submit" name="" id="" class="btn btn-primary" value="Submit">
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import moment from 'moment'

export default {
  name: 'Poll',
  data () {
    return {
      loading: true,
      poll: Object
    }
  },
  computed: {
    createdDate: function () {
      return this.poll.created_date
    }
  },
  mounted () {
    axios.get('http://localhost:3000/api/polls/' + this.$route.params.id)
      .then(res => {
        this.loading = false
        this.poll = res.data
      })
  },
  filters: {
    formatDate: function (date) {
      return moment().format('MMM Do YYYY')
    }
  }
}
</script>

<style>
.poll-wrapper{
  width: 100%;
  background-color: papayawhip;
  padding: 18px;
  box-shadow: 3px 3px 3px #eee;
}
.options{
  margin: 20px;
  padding: 0;
}
.options li{
  list-style: none;
  padding: 6px;
}
</style>
