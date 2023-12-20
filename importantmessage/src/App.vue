<template>
  <div>
    <div class="firstrun" v-on:click="secondstage">
      <div class="heart">
        <img class="heartimg" v-show="!notright && !thirdstage" v-bind:class="[{heartbeat: isheartbeat, heartup: isheartup, heartdown: isheartdown}, {pulse: isPulse, notpulse: !isPulse}, {heartsizemax: thirdstage, heartopac: thirdstage} ]" src="./assets/heart800px.png" alt="Сердечко">
        <img class="heartimg" v-show="notright" v-bind:class="{heartbeat: isheartbeat, heartup: isheartup, pulse: isSecondStagebroken, shake: notright}" src="./assets/brokenheart800px.png" alt="Сердечко">
        <img class="heartimg" v-if="thirdstage" v-bind:class="[{heartbeat: isheartbeat, heartup: isheartup, heartdown: isheartdown}, {heartsizemax: thirdstage, heartopac: thirdstage} ]" src="./assets/heart800px.png" alt="Сердечко">
      </div>
      <div class="bgheart" v-if="isheartbeat">
        <img class="heartimgbg" v-if="isheartbeat" src="./assets/heart800px.png" alt="Сердечко">
      </div>
      <div class="bgheart2" v-if="isheartbeat">
        <img class="heartimgbg2" v-if="isheartbeat" src="./assets/heart800px.png" alt="Сердечко">
      </div>
      <div class="underhearttext" v-bind:class="{hiden: !showheartbeattext}">
        <h2 class="underhearttexth2">Нажми на меня...</h2>
      </div>
      <div class="paswblock" @keyup.enter="openheartfun()" v-bind:class="{unhiden: !openSecondStageText, hiden: close}">
        <h2 class="wt" v-show="!notrightext">Сердечко закрыто🔒</h2>
        <p class="gt" v-show="!notrightext">Введи пароль, чтобы разблокировать его:</p>
        <h2 class="wt" v-show="notrightext">Неверный пароль(</h2>
        <p class="gt" v-show="notrightext">Попробуй еще раз:</p>
        <input class="passwinput" v-model="password" type="text" placeholder="Пароль">
        <button class="openbutton" :disabled="!password.length" v-on:click="openheartfun">Открыть</button>
      </div>
      <div class="govstrtext" v-bind:class="{show: thirdstage, hiden: !thirdstage}">
        <h1 class="govstr">Го встр?)</h1>
      </div>
      <div class="topext" v-show="thirdstage">
        <h2>Влад ❤️ Маня</h2>
      </div>
      <div class="bottext" v-show="thirdstage">
        <h2>23.12.23</h2>
      </div>

    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return {
    isheartbeat: true,
    showheartbeattext: true,
    isSecondStage: false,
    isheartup: false,
    isheartdown: false,
    openSecondStageText: false,
    password: '',
    notright: false,
    notrightext: false,
    isSecondStagebroken: false,
    close: false,
    thirdstage: false,
    isPulse: false
  }
  },
  methods:{
    secondstage(){
      this.isheartbeat = false
      this.isheartup = true
      this.showheartbeattext = false
      this.isSecondStage = true
      this.isPulse = true
      let cont = this
      function unhidenSST(){
        cont.openSecondStageText = true
      }
      setTimeout(unhidenSST, 1000)
    },
    openheartfun(){
      let cont = this
      function notrightunsv(){
        cont.notright = false
        console.log("wrong");
      }
    if ((this.password).toLowerCase() == "маша"){
      console.log("Маша");
      this.close = true
      this.isheartdown = true
      console.log(this.isheartup);
      this.thirdstage = true
      this.isPulse = false
    }
    else {
      let cont = this
      cont.notright = true
      cont.notrightext = true
      
      setTimeout(notrightunsv, 1000)
      
      
    }
  }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100vh;
  background: rgb(80,12,12);
  background: linear-gradient(345deg, rgba(80,12,12,1) 4%, rgba(15,15,15,1) 79%);

}
* {
  margin: 0;
  padding: 0;
}
.heartimg {
  width: 35vw;
  
}
.heartbeat {
  animation: heartbeat 3000ms infinite;
}
.firstrun {
  display: flex;
  height: 100vh;
}
.heart {
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 2;
  width: 100%;
}
.bgheart {
  position: fixed;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  width: 100%;
  z-index: 1;
}
.heartimgbg {
  width: 55vw;
  opacity: 0.12;
  animation: heartbeatbg 3000ms infinite ease-in-out;
  transition: 200ms;
}
.bgheart2 {
  position: fixed;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  width: 100%;
  z-index: 1;
}
.heartimgbg2 {
  width: 55vw;
  opacity: 0.12;
  animation: heartbeatbg2 3000ms infinite ease-in-out;
  transition: 200ms;
}
.underhearttext {
  position: fixed;
  width: 100%;
  font-size: 2vw;
  display: flex;
  /* height: 100%; */
  /* align-items: center; */
  justify-content: center;
  padding-top: 80vh;
  color: #A50C40;
  transition: 500ms;
}

.hiden{
  opacity: 0;
  transition: 1000ms;
}
.unhiden {
  opacity: 0;
  transition: 2000ms;
}
.pulse {
  animation: pulse 3000ms infinite;
}

.underhearttexth2 {
  animation: heartbeattext 3000ms infinite;
}
.heartup {
  padding-bottom: 20%;
  transition: 1000ms;
}
.paswblock {
  position: fixed;
  width: 100%;
  font-size: 3vh;
  display: flex;
  flex-direction: column;
  padding-top: 60vh;
  transition: 500ms;
  align-items: center;
  z-index: 5;
  
}
.gt {
  color: #8C8C8C;
  margin-bottom: 2%;
}
.wt {
  color: #FFFFFF;
  margin-bottom: 1%;
}
.passwinput {
  font-size: 3vh;
  background-color: transparent;
  border: 0;
  border-bottom: solid 15px #610221;
  outline: none;
  padding: 20px;
  color: #FFFFFF;
  font-weight: bold;
  transition: 500ms;
  margin-bottom: 4%;
  text-align: center;
}
input:focus {
    border-bottom: 15px solid #FF0C5E;
    transition: 500ms;
}

::placeholder {
    color: #610221;
    font-weight: 300;
}

.openbutton {
  padding: 1% 2%;
  font-size: 4vh;
  background-color: transparent;
  border: solid 15px #FF0C5E;
  border-radius: 50px;
  color: #FF0C5E;
  font-weight: bold;
  cursor: pointer;
  transition: 500ms;
}

.openbutton:disabled {
  border: solid 15px #610221;
  color: #610221;
  cursor: default;
  transition: 500ms;
}

.shake  {
  animation: shake 500ms;
}

.heartdown {
  padding-bottom: 0;
  transition: 1000ms;
}
.heartsizemax {
  width: 52.5%;
  animation: hearsizemax 1000ms;
  opacity: 0.12;
}
/* .heartopac{
  opacity: 0.12;
  animation: hearopac 1000ms;
} */

.govstrtext {
  position: fixed;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100%;
  z-index: 4;
  opacity: 0;
}
.govstr {
  font-size: 9vh;
  color: #FFFFFF;
}
.show {
  opacity: 1;
  animation: show 1000ms;
}
.topext {
  position: fixed;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  z-index: 6;
  padding-top: 2%;
  font-size: 1vw;
  font-weight: bold;
  color: #FFFFFF;
  opacity: 0.7;
}
.bottext {
  position: fixed;
  display: flex;
  align-items: flex-end;
  justify-content: center;
  width: 100%;
  height: 100%;
  z-index: 7;
  font-size: 1vw;
  font-weight: bold;
  color: #a30238;
}


@keyframes heartbeat {
    0%{
      width: 35vw;
    }
    15% {
      width: 40vw;
    }
    30%{
      width: 35vw;
    }
    50%{
      width: 40vw;
    }
    70%{
      width: 35vw;
    }
    
}
@keyframes pulse {
    0%{
      width: 35%;
    }
    50%{
      width: 37.5%;
    }
    
}

/* 500px */
@keyframes heartbeat500 {
    0%{
      width: 50vw;
    }
    15% {
      width: 60vw;
    }
    30%{
      width: 50vw;
    }
    50%{
      width: 60vw;
    }
    70%{
      width: 50vw;
    }
    
}
@keyframes pulse500 {
    0%{
      width: 50vw;
    }
    50%{
      width: 55vw;
    }
    
}
@keyframes heartbeatbg500 {
    0%{
      width: 60vw;
      opacity: 0.12;
    }
    15% {
      width: 65vw;
      opacity: 0.10;
    }
    30%{
      width: 70vw;
      opacity: 0.07;
    }
    50%{
      width: 75vw;
      opacity: 0.03;
    }
    70%{
      width: 80vw;
      opacity: 0;
    }
    80%{
      width: 60vw;
      opacity: 0;
    }
    
}
@keyframes heartbeatbg2_500 {
    0%{
      opacity: 0;
      width: 60vw;
    }
    15% {
      opacity: 0;
      width: 60vw;
    }
    30% {
      opacity: 0.12;
      width: 60vw;
    }
    50%{
      opacity: 0.10;
      width: 60vw;
    }
    70% {
      opacity: 0.07;
      width: 65vw;
    }
    80% {
      width: 70vw;
      opacity: 0.03;
    }
    90% {
      width: 75vw;
      opacity: 0;
    }
    100% {
      width: 75vw;
      opacity: 0;
    }

    
}
@keyframes heartbeattext500 {
    0%{
      font-size: 5vw;
      color: #A50C40;
    }
    15% {
      font-size: 5.3vw;
      color: #ce0a4b;
    }
    30%{
      font-size: 5vw;
      color: #A50C40;
    }
    50%{
      font-size: 5.3vw;
      color: #ce0a4b;
    }
    70%{
      font-size: 5vw;
      color: #A50C40;
    }
    100% {
      font-size: 5vw;
    }
    
}
@keyframes hearsizemax500 {
  0%{
    width: 50vw;
    opacity: 1;
  }
  10%{
    width: 52.5vw;
  }
  20%{
    width: 55vw;
  }
  30%{
    width: 57.5vw;
  }
  40%{
    width: 60vw;
  }
  50%{
    width: 62.5vw;
  }
  60%{
    width: 65vw;
  }
  70%{
    width: 67.5vw;
  }
  80% {
    opacity: 1;
  }
  90%{
    opacity: 0.5;
  }
  100%{
    width: 67.5vw;
  }
}


@keyframes shake {
    0%{
      padding-left: 10%;
    }
    25%{
      padding-left: 0;
    }
    50%{
      padding-right: 10%;
    }
    75% {
      padding-right: 0;
    }
    
}

@keyframes heartbeattext {
    0%{
      font-size: 2vw;
      color: #A50C40;
    }
    15% {
      font-size: 2.3vw;
      color: #ce0a4b;
    }
    30%{
      font-size: 2vw;
      color: #A50C40;
    }
    50%{
      font-size: 2.3vw;
      color: #ce0a4b;
    }
    70%{
      font-size: 2vw;
      color: #A50C40;
    }
    100% {
      font-size: 2vw;
    }
    
}


@keyframes heartbeatbg {
    0%{
      width: 45%;
      opacity: 0.12;
    }
    15% {
      width: 50%;
      opacity: 0.10;
    }
    30%{
      width: 55%;
      opacity: 0.07;
    }
    50%{
      width: 60%;
      opacity: 0.03;
    }
    70%{
      width: 65%;
      opacity: 0;
    }
    80%{
      width: 45%;
      opacity: 0;
    }
    
}

@keyframes heartbeatbg2 {
    0%{
      opacity: 0;
      width:  45%;
    }
    15% {
      opacity: 0;
      width: 45%;
    }
    30% {
      opacity: 0.12;
      width: 45%;
    }
    50%{
      opacity: 0.10;
      width: 50%;
    }
    70% {
      opacity: 0.07;
      width: 55%;
    }
    80% {
      width: 60%;
      opacity: 0.03;
    }
    90% {
      width: 65%;
      opacity: 0;
    }
    100% {
      width: 65%;
      opacity: 0;
    }

    
}

@keyframes hearsizemax {
  0%{
    width: 35%;
    opacity: 1;
  }
  10%{
    width: 37.5%;
  }
  20%{
    width: 40%;
  }
  30%{
    width: 42.5%;
  }
  40%{
    width: 45%;
  }
  50%{
    width: 47.5%;
  }
  60%{
    width: 50%;
  }
  70%{
    width: 52.5%;
  }
  80% {
    opacity: 1;
  }
  90%{
    opacity: 0.5;
  }
  100%{
    width: 52.5%;
  }
}
@keyframes hearopac {
  0%{
    opacity: 1;
  }
  80% {
    opacity: 1;
  }
  90%{
    opacity: 0.5;
  }
  100%{
    opacity: 0.12;
  }
}
@keyframes show {
  0%{
    opacity: 0;
  }
  80% {
    opacity: 0;
  }
  90%{
    opacity: 0.5;
  }
  100%{
    opacity: 1;
  }
}

@media only screen and (max-width: 1200px) {
  
}
@media only screen and (max-width: 900px) {

}
@media only screen and (max-width: 600px) {

}
@media only screen and (max-width: 500px) {
  .heartimg {
     width: 50vw;
  }
  .heartbeat {
    animation: heartbeat500 3000ms infinite;
  }
  .pulse {
  animation: pulse500 3000ms infinite;
  }
  .heartimgbg {
  width: 60vw;
  opacity: 0.12;
  animation: heartbeatbg500 3000ms infinite ease-in-out;
  transition: 200ms;
  }
  .heartimgbg2 {
  width: 60vw;
  opacity: 0.12;
  animation: heartbeatbg2_500 3000ms infinite ease-in-out;
  transition: 200ms;
  }
  .underhearttext {
    font-size: 5vw;
  }
  .underhearttexth2 {
  animation: heartbeattext500 3000ms infinite;
  }
  .paswblock {
    font-size:large;
  }
  .passwinput {
    border-bottom: solid 2px #610221;
    width: 45%;
    padding: 13px;
  }
  input:focus {
    border-bottom: 2px solid #FF0C5E;
    transition: 500ms;
  }
  .openbutton {
    padding: 4% 6%;
    font-size: 3vh;
    background-color: transparent;
    border: solid 2px #FF0C5E;
    border-radius: 21px;
  }
  .openbutton:disabled {
    border: solid 2px #610221;
    color: #610221;
  }
  .heartsizemax {
    /* width: 52.5%; */
    width: 67.5vw;
    animation: hearsizemax500 1000ms;
    opacity: 0.12;
  }
  .govstr {
    font-size: 7vh;
  }
  .bottext {
    font-size: 5vw;
  }
  .topext {
    font-size: 4vw;
  }
}
</style>


