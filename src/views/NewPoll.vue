<template>
  <div class="about card clearfix">
    <div id="msg" class="text-center"><h3>{{ message }}</h3></div>
    <h1 class="text-center">New Poll</h1>
    <form @submit.prevent="saveNewPoll">
      <div class="form-group">
        <label for="poll_text">Title</label>
        <input type="text" name="poll_text" id="poll_text" v-model="poll_text" class="form-control" />
      </div>
      <div class="form-group">
        <label for="ending_date">Ending Date</label>
        <input type="date" name="ending_date" id="ending_date" v-model="ending_date" class="form-control" />
      </div>
      <br>
      <h3 class="text-center"><span class="plus" @click="increaseCounter">+</span> Options <span class="minus" @click="decreaseCounter">-</span></h3>
      <div class="form-group" v-for="count in options_count" :key="count">
        <label for="poll_text">Option #{{ count }}</label>
        <input type="text" name="poll_text" id="poll_text" v-model="options[count]" class="form-control" />
      </div>
      <input type="submit" name="" id="" class="btn btn-primary right" value="Submit">
    </form>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'NewPoll',
  data () {
    return {
      poll_text: '',
      ending_date: '',
      options: [],
      options_count: 2,
      message: ''
    }
  },
  methods: {
    saveNewPoll () {
      const poll = {
        poll_text: this.poll_text,
        ending_date: this.ending_date,
        options: this.options,
        is_published: true,
        author: '5e915ce31c9d4400002d2c29'
      }

      if (this.poll_text.length && this.ending_date && this.options.length) {
        axios.post('http://localhost:3000/api/polls', poll)
          .then(res => {
            this.message = res.message
          })
      } else {
        this.message = 'Please Fill up all the fields'
      }
    },
    increaseCounter () {
      if (this.options_count < 5) {
        this.options_count++
      }
    },
    decreaseCounter () {
      if (this.options_count > 2) {
        this.options_count--
      }
    }
  }
}
</script>

<style scoped>
.about{
  width: 70%;
  margin: 0 auto;
}
#options-wrapper{
  display: flex;
}
.option-inp {
  width: auto;
}
.plus {
  font-size: 22px;
  background-color: #f7d7a2;
  padding: 5px 10px;
  cursor: pointer;
}
.minus {
  font-size: 22px;
  background-color: #f7d7a2;
  padding: 5px 12px;
  cursor: pointer;
}
</style>
