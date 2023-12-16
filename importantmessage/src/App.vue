<template>
  <div>
    <div class="firstrun" v-on:click="secondstage">
      <div class="heart">
        <img class="heartimg" v-bind:class="{heartbeat: isheartbeat, heartup: isSecondStage, pulse: isSecondStage}" src="./assets/heart.png" alt="Сердечко">
      </div>
      <div class="bgheart" v-if="isheartbeat">
        <img class="heartimgbg" v-if="isheartbeat" src="./assets/heart.png" alt="Сердечко">
      </div>
      <div class="bgheart2" v-if="isheartbeat">
        <img class="heartimgbg2" v-if="isheartbeat" src="./assets/heart.png" alt="Сердечко">
      </div>
      <div class="underhearttext" v-bind:class="{hiden: !showheartbeattext}">
        <h2 class="underhearttexth2">Нажми на меня...</h2>
      </div>
      <div class="paswblock" v-bind:class="{unhiden: !openSecondStageText}">
        <h2 class="wt">Сердечко закрыто🔒</h2>
        <p class="gt">Введи пароль, чтобы разблокировать его:</p>
        <input class="passwinput" type="text" placeholder="Пароль">
        <button class="openbutton">Открыть</button>
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
    openSecondStageText: false
  }
  },
  methods:{
    secondstage(){
      this.isheartbeat = false
      this.showheartbeattext = false
      this.isSecondStage = true
      let cont = this
      function unhidenSST(){
        cont.openSecondStageText = true
      }
      setTimeout(unhidenSST, 1000)
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
  width: 35%;
  
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
}
.bgheart {
  position: fixed;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  z-index: 1;
}
.heartimgbg {
  width: 45%;
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
  z-index: 1;
}
.heartimgbg2 {
  width: 45%;
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
}


@keyframes heartbeat {
    0%{
      width: 35%;
    }
    15% {
      width: 40%;
    }
    30%{
      width: 35%;
    }
    50%{
      width: 40%;
    }
    70%{
      width: 35%;
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
</style>


