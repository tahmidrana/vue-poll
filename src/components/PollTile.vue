<template>
  <div class="poll-tile">
    <h3 class="poll-title"><router-link :to="{ name: 'view-poll', params: { title: slugifiedTitle, id: poll._id } }" :poll="poll">{{ poll.poll_text }}</router-link></h3>
    <p class="poll-feat">Posted on <span class="poll-date">{{ poll.created_date|formatDate }}</span> By <span class="poll-author">{{ poll.author.name }}</span></p>
    <p class="poll-response">Total Response# 130</p>
  </div>
</template>

<script>
import moment from 'moment'
export default {
  name: 'PollTile',
  props: {
    poll: Object
  },
  computed: {
    slugifiedTitle: function () {
      return this.poll.poll_text.split(' ').join('-').toLowerCase()
    }
  },
  filters: {
    formatDate: function (date) {
      return moment().format('MMM Do YYYY')
    }
  }
}
</script>

<style>
.poll-tile{
    padding: 0;
    margin: 15px 0;
    background-color: papayawhip;
    padding: 10px;
    box-shadow: 2px 2px 2px #eee;
    text-align: center;
}
.poll-title{
    margin: 10px 0;
    padding: 0;
}
.poll-feat{
    font-size: 14px;
    margin: 0;
    padding: 0;
}
.poll-author{
    color: #42b983;
}
.poll-response{
    margin: 8px 0;
}
</style>
