<template>
  <form @submit.prevent="submitForm">

    <div class="form-control" :class="{ invalid: userNameValidaty == 'invalied' }">
      <label for="user-name">Your Name</label>
      <input id="user-name" v-model="userName" @blur="validateInput" name="user-name" type="text" />
      <p v-show="userNameValidaty == 'invalied'">please enter a valid name</p>
    </div>
    <div class="form-control">
      <label for="age">Your Age (Years)</label>
      <input id="age" name="age" type="number" v-model="userAge" />
    </div>
    <div class="form-control">
      <label for="referrer">How did you hear about us?</label>
      <select id="referrer" name="referrer" v-model="referrer">
        <option value="google">Google</option>
        <option value="wom">Word of mouth</option>
        <option value="newspaper">Newspaper</option>
      </select>
    </div>
    <div class="form-control">
      <h2>What are you interested in?</h2>
      <div>
        <input id="interest-news" value="news" name="interest" v-model="interest" type="checkbox" />
        <label for="interest-news">News</label>
      </div>
      <div>
        <input id="interest-tutorials" value="tutorials" name="interest" v-model="interest" type="checkbox" />
        <label for="interest-tutorials">Tutorials</label>
      </div>
      <div>
        <input id="interest-nothing" value="nothing" name="interest" v-model="interest" type="checkbox" />
        <label for="interest-nothing">Nothing</label>
      </div>
    </div>
    <div class="form-control">
      <h2>How do you learn?</h2>
      <div>
        <input id="how-video" value="video" name="how" v-model="how" type="radio" />
        <label for="how-video">Video Courses</label>
      </div>
      <div>
        <input id="how-blogs" value="blogs" name="how" v-model="how" type="radio" />
        <label for="how-blogs">Blogs</label>
      </div>
      <div>
        <input id="how-other" value="other" name="how" v-model="how" type="radio" />
        <label for="how-other">Other</label>
      </div>
      <div>
        <input id="confirm-use"  name="confirmation" v-model="confirm" type="checkbox" />
        <label for="confirm-use">confirmation for Learning</label>
      </div>
      
      <div class="form-control">
      <rating-control v-model="rating" ></rating-control>
      </div>
    </div>
    <div>
      <button>Save Data</button>
    </div>
  </form>
</template>

<script>
import RatingControl from './RatingControl.vue'
export default {
  data() {
    return {
      userName: '',
      userAge: '',
      referrer: 'wom',
      interest: [],
      how: null,
      userNameValidaty: 'pending',
      rating:null,
      confirm:false
    }
  },
  methods: {
    submitForm() {
      console.log(this.rating);
      console.log(this.confirm);
      this.rating=null
    },
    validateInput() {
      if (this.userName.trim() === '') {
        this.userNameValidaty = 'invalied'
      }
      else {
        this.userNameValidaty = 'valied'
      }
    }
  },
  components:{
    RatingControl
  }
}
</script>

<style scoped>
form {
  margin: 2rem auto;
  max-width: 40rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 2rem;
  background-color: #ffffff;
}

.form-control {
  margin: 0.5rem 0;
}

.form-control.invalid input {
  border-color: red;
}

.form-control.invalid label {
  color: red;
}

label {
  font-weight: bold;
}

h2 {
  font-size: 1rem;
  margin: 0.5rem 0;
}

input,
select {
  display: block;
  width: 100%;
  font: inherit;
  margin-top: 0.5rem;
}

select {
  width: auto;
}

input[type='checkbox'],
input[type='radio'] {
  display: inline-block;
  width: auto;
  margin-right: 1rem;
}

input[type='checkbox']+label,
input[type='radio']+label {
  font-weight: normal;
}

button {
  font: inherit;
  border: 1px solid #0076bb;
  background-color: #0076bb;
  color: white;
  cursor: pointer;
  padding: 0.75rem 2rem;
  border-radius: 30px;
}

button:hover,
button:active {
  border-color: #002350;
  background-color: #002350;
}
</style>