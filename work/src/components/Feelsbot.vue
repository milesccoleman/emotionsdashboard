<template>

  <div id="emotions">
  <img v-if='gifSrc != null' id="gif" v-bind:src="gifSrc"/>
      <div class="emotion" id="angry" v-bind:style="{backgroundColor: angry}"></div><br><br>
      <div class="emotion" id="happy" v-bind:style="{backgroundColor: happy}"></div><br><br><br><br>

    <form v-on:submit.prevent="getDataDoStuffWithData">
      <div id="output" class="fakeScreen"><p class="line1">$ {{msg}}
        <span v-bind:style="{ 'color': angry }">{{msg1}}</span>
        <span v-bind:style="{ 'color': happy }">{{msg2}}</span>
        <span v-bind:style="{ 'color': sad }">{{msg3}}</span>
        <span v-bind:style="{ 'color': fearful }">{{msg4}}</span>
        <span v-bind:style="{ 'color': surprised }">{{msg5}}</span>
        <span class="cursor1">_</span></p>
      </div>
        <input id="textWindow" v-on:keyup="resetTimer" type="text" v-bind:style="{color: color}" v-model="emotion" placeholder="tell me something"/>
    </form>

      <div class="emotion" id="sad" v-bind:style="{backgroundColor: sad}"></div><br><br>
      <div class="emotion" id="fearful" v-bind:style="{backgroundColor: fearful}"></div><br><br>
      <div class="emotion" id="surprised" v-bind:style="{backgroundColor: surprised}"></div><br><br><br><br>
  </div>

</template>

<script>
import axios from 'axios'
export default {
  name: 'Feelsbot',
  data () {
    return {
      color: '',
      emotion: '',
      angry: '',
      happy: '',
      sad: '',
      fearful: '',
      surprised: '',
      msg: 'tell me anything you want, and i\'ll tell you how it makes me feel',
      msg1: '',
      msg2: '',
      msg3: '',
      msg4: '',
      msg5: '',
      time: 0,
      gif: [],
      gifSrc: null,
      output: 0,
      guider: 'robot',
      guider2: 'machine cyborg',
      video: false,
      file: ''
    }
  },
  methods: {
    getDataDoStuffWithData: function () {
      var self = this

      const formData = new FormData();
        formData.append('app_key', 'd08c791a788349a4bcfcaec6818a1c76');
        formData.append('url', 'https://static1.squarespace.com/static/569295f525981daa98f80256/5727b751d210b8a998423309/5727b752859fd05df76bfb14/1462220660854/John+Hinds+Smiling.jpg?format=1000w');
      axios.post("https://api-face.sightcorp.com/api/detect/", formData)
    .then(function (result) {
      console.log(result);
    }, function (error) {
      console.log(error);
    });
}
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import url("https://fonts.googleapis.com/css?family=Proza+Libre|Fira+Mono");
.fakeScreen {
  background-color: #151515;
  box-sizing: border-box;
  width: 550px;
  margin: 0 auto;
  padding: 20px;
  border-bottom-left-radius: 5px;
  border-bottom-right-radius: 5px;
  margin-top: -260px;
  margin-bottom: 25px;
  z-index: 1;
}
#gif {
}
img {
  height: 400px;
  margin-bottom:  -775px;
  border: black;
}
p {
  position: relative;
  left: 50%;
  margin-left: -8.5em;
  text-align: left;
  font-size: 1.25em;
  font-family: monospace;
  white-space: normal;
  overflow: hidden;
  width: 0;
}
span {
  color: #fff;
  font-weight: bold;
}
@keyframes type {
  to {
    width: 17em;
  }
}
.line1 {
  color: #9CD9F0;
  -webkit-animation: type .5s 1s steps(20, end) forwards;
  -moz-animation: type .5s 1s steps(20, end) forwards;
  -o-animation: type .5s 1s steps(20, end) forwards;
  animation: type .5s 1s steps(20, end) forwards;
}
@keyframes blink {
  0% {
    opacity: 0;
  }
  40% {
    opacity: 0;
  }
  50% {
    opacity: 1;
  }
  90% {
    opacity: 1;
  }
  100% {
    opacity: 0;
  }
}
.cursor1 {
  -webkit-animation: blink 1s 2s 2 forwards;
  -moz-animation: blink 1s 2s 2 forwards;
  -o-animation: blink 1s 2s 2 forwards;
  animation: blink 1s 2s 2 forwards;
  -webkit-animation-iteration-count: infinite;
}
html, body, #emotions {
  background: black;
}
@keyframes angerPulse {
  from {-webkit-box-shadow: 0 0 9px #ff3f3f; }
  50% {-webkit-box-shadow: 0 0 36px #ff3f3f; }
  to {-webkit-box-shadow: 0 0 9px #ff3f3f; }
}
#emotions {
  margin-top: -25px;
}
#angry {
  height: 125px;
  z-index: -1;
  -webkit-animation-name: angerPulse;
  -webkit-animation-duration: 3s;
  -webkit-animation-iteration-count: infinite;
  margin-top: 15px;
  }
@keyframes happyPulse {
  from {-webkit-box-shadow: 0 0 9px #2bd1fc; }
  50% {-webkit-box-shadow: 0 0 36px #2bd1fc; }
  to {-webkit-box-shadow: 0 0 9px #2bd1fc; }
}
#happy {
  height: 125px;
  z-index: -1;
  -webkit-animation-name: happyPulse;
  -webkit-animation-duration: 1.5s;
  -webkit-animation-iteration-count: infinite;
}
@keyframes sadPulse {
  from {-webkit-box-shadow: 0 0 9px #c04df9; }
  50% {-webkit-box-shadow: 0 0 36px #c04df9; }
  to {-webkit-box-shadow: 0 0 9px #c04df9; }
}
#sad {
  height: 125px;
  z-index: -1;
  -webkit-animation-name: sadPulse;
  -webkit-animation-duration: 2s;
  -webkit-animation-iteration-count: infinite;
}
@keyframes fearfulPulse {
  from {-webkit-box-shadow: 0 0 9px #f3ea5f; }
  50% {-webkit-box-shadow: 0 0 36px #f3ea5f; }
  to {-webkit-box-shadow: 0 0 9px #f3ea5f; }
}
#fearful {
  height: 125px;
  z-index: -1;
  -webkit-animation-name: fearfulPulse;
  -webkit-animation-duration: 2s;
  -webkit-animation-iteration-count: infinite;
}
@keyframes surprisedPulse {
  from {-webkit-box-shadow: 0 0 9px #42f459; }
  50% {-webkit-box-shadow: 0 0 36px #42f459; }
  to {-webkit-box-shadow: 0 0 9px #42f459; }
}
#surprised {
  height: 125px;
  z-index: -1;
  -webkit-animation-name: surprisedPulse;
  -webkit-animation-duration: 2s;
  -webkit-animation-iteration-count: infinite;
}
input {
  padding: 1rem 1rem;
  font-size: 2rem;
  border: 0;
  border-radius: 3px;
  background: #fff;
  z-index: 1;
}
form {
}
input[type="color"] {
  width: 40px;
  border: 1px solid black;
  margin: 0px;
  padding: 0px !important;
  height: 40px;
}
</style>
