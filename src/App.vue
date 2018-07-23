<template>
  <div id="app">
    <main class="felt noselect"> 
      <div class="player-wrapper">
        <div class="player-container">
          <div
            :class="{'player-turn' : playerOne.hasTurn}"
            class="player-info">
            <div class="player-name">
              <h2>{{playerOne.name}}</h2>
            </div>
            <div class="player-score">
              <h1>{{playerOneScore}}</h1>
            </div>
          </div>
          <div class="player-history">
            <span v-for="(ball, index) in playerOne.shotHistory"
              :key="index">
              <red-ball v-if="ball.colour === 'red'" class="history-ball"/>
              <yellow-ball v-if="ball.colour === 'yellow'" class="history-ball"/>
              <green-ball v-if="ball.colour === 'green'" class="history-ball"/>
              <brown-ball v-if="ball.colour === 'brown'" class="history-ball"/>
              <blue-ball v-if="ball.colour === 'blue'" class="history-ball"/>
              <pink-ball v-if="ball.colour === 'pink'" class="history-ball"/>
              <black-ball v-if="ball.colour === 'black'" class="history-ball"/>
              <span v-if="ball.colour === 'foul'" class="foulshot">{{ball.points}}</span>
            </span>
          </div>
        </div>
        <div class="player-container">
          <div
            :class="{'player-turn' : playerTwo.hasTurn}"
            class="player-info">
            <div class="player-name">
              <h2>{{playerTwo.name}}</h2>
            </div>
            <div class="player-name">
              <h1>{{playerTwoScore}}</h1>
            </div>
          </div>
          <div class="player-history">
            <span
              v-for="(ball, index) in playerTwo.shotHistory"
              :key="index">
              <red-ball v-if="ball.colour === 'red'" class="history-ball"/>
              <yellow-ball v-if="ball.colour === 'yellow'" class="history-ball"/>
              <green-ball v-if="ball.colour === 'green'" class="history-ball"/>
              <brown-ball v-if="ball.colour === 'brown'" class="history-ball"/>
              <blue-ball v-if="ball.colour === 'blue'" class="history-ball"/>
              <pink-ball v-if="ball.colour === 'pink'" class="history-ball"/>
              <black-ball v-if="ball.colour === 'black'" class="history-ball"/>
              <div v-if="ball.colour === 'foul'" class="foulshot">{{ball.points}}</div>
            </span>
          </div>
        </div>
      </div>
      <div class="ball-container">
        <div class="left-side">
          <div>
            <div
              @click="potBall('red')"
              class="red-ball-container">
              <red-ball class="red-ball pointer ball" :class="{'on-ball' : redBallCount > 0}"/>
              <span class="red-ball-counter pointer">
                {{redBallCount}}
              </span>
            </div>
          </div>
        </div>
        <div class="colour-triangle">
          <div class="top-row">
            <div @click="potBall('black')">
              <black-ball class="pointer ball" :class="{'on-ball' : blackBall.on}"/>              
            </div>
          </div>
          <div class="middle-row">
            <div @click="potBall('pink')">
              <pink-ball class="pointer ball" :class="{'on-ball' : pinkBall.on}"/>              
            </div>
            <div @click="potBall('blue')">
              <blue-ball class="pointer ball" :class="{'on-ball' : blueBall.on}"/>
            </div>
          </div>
          <div class="bottom-row">
            <div @click="potBall('yellow')">
              <yellow-ball class="pointer ball" :class="{'on-ball' : yellowBall.on}"/>
            </div>
            <div @click="potBall('green')">
              <green-ball  class="pointer ball" :class="{'on-ball' : greenBall.on}"/>
            </div>
            <div @click="potBall('brown')">
              <brown-ball class="pointer ball" :class="{'on-ball' : brownBall.on}"/>
            </div>
          </div>
        </div>
      </div>
      <div class="action-buttons">
        <div class="buttons">
          <a class="pointer btn btn-foul">FOUL</a>
          <a @click="undo" class="pointer btn btn-undo">UNDO</a>
          <a @click="switchPlayer" class="pointer btn btn-switch">SWITCH PLAYER</a>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
import RedBall from './components/svg/RedBall';
import YellowBall from './components/svg/YellowBall';
import GreenBall from './components/svg/GreenBall';
import BrownBall from './components/svg/BrownBall';
import BlueBall from './components/svg/BlueBall';
import PinkBall from './components/svg/PinkBall';
import BlackBall from './components/svg/BlackBall';

export default {
  name: 'app',
  components: {
    RedBall,
    YellowBall,
    GreenBall,
    BrownBall,
    BlueBall,
    PinkBall,
    BlackBall,
  },
  data() {
    return {
      playerOne: {
        name: 'Michael',
        hasTurn: true,
        shotHistory: [],
      },
      playerTwo: {
        name: 'Tom',
        hasTurn: false,
        shotHistory: [],
      },
      redBall: {
        quantity: 10,
        on: true,
        points: 1,
      },
      yellowBall: {
        quantity: 1,
        on: false,
        points: 2,
      },
      greenBall: {
        quantity: 1,
        on: false,
        points: 3,
      },
      brownBall: {
        quantity: 1,
        on: false,
        points: 4,
      },
      blueBall: {
        quantity: 1,
        on: false,
        points: 5,
      },
      pinkBall: {
        quantity: 1,
        on: false,
        points: 6,
      },
      blackBall: {
        quantity: 1,
        on: false,
        points: 7,
      },
      colourRun: false,
      lastPottedOnColourRun: null,
    };
  },
  computed: {
    redBallCount() {
      return this.redBall.quantity;
    },
    redBallCountPadLeft() {
      return this.redBallCount < 10;
    },
    playerOneScore() {
      return this.playerOne.shotHistory.reduce((carry, shot) => carry + shot.points, 0);
    },
    playerTwoScore() {
      return this.playerTwo.shotHistory.reduce((carry, shot) => carry + shot.points, 0);
    },
  },
  methods: {
    potBall(colour) {
      if (colour === 'red' && this.redBallCount === 0) return;
      if (colour === 'yellow' && this.yellowBall.on === false) return;
      if (colour === 'green' && this.greenBall.on === false) return;
      if (colour === 'brown' && this.brownBall.on === false) return;
      if (colour === 'blue' && this.blueBall.on === false) return;
      if (colour === 'pink' && this.pinkBall.on === false) return;
      if (colour === 'black' && this.blackBall.on === false) return;

      if (this.colourRun) this.handleColourRun(colour);
      if (this.playerOne.hasTurn) this.playerOne.shotHistory.push(this.newBall(colour));
      if (this.playerTwo.hasTurn) this.playerTwo.shotHistory.push(this.newBall(colour));

      if (colour === 'red') this.handlePotRed();
      if (colour !== 'red' && this.colourRun === false) this.toggleColours(false);
      if (colour !== 'red' && this.redBallCount === 0 && this.colourRun === false) this.startColourRun();
    },
    handlePotRed() {
      this.decrementRedBallCount();
      this.toggleColours(true);
    },
    toggleColours(status) {
      this.yellowBall.on = status;
      this.greenBall.on = status;
      this.brownBall.on = status;
      this.blueBall.on = status;
      this.pinkBall.on = status;
      this.blackBall.on = status;
    },
    startColourRun() {
      this.colourRun = true;
      this.toggleColours(false);
      this.yellowBall.on = true;
    },
    handleColourRun(colour) {
      this.toggleColours(false);
      if (colour === 'yellow') this.greenBall.on = true;
      if (colour === 'green') this.brownBall.on = true;
      if (colour === 'brown') this.blueBall.on = true;
      if (colour === 'blue') this.pinkBall.on = true;
      if (colour === 'pink') this.blackBall.on = true;
      if (colour === 'black') this.completeMatch();
    },
    newBall(colour) {
      return {
        colour,
        points: this.getPointsByColour(colour),
      };
    },
    undo() {
      let last = {};
      if (this.playerOne.hasTurn) {
        last = this.playerOne.shotHistory.splice(-1)[0];
      }
      if (this.playerTwo.hasTurn) {
        last = this.playerTwo.shotHistory.splice(-1)[0];
      }

      if (last.colour === 'red') {
        this.redBall.quantity += 1;
      }
    },
    switchPlayer() {
      this.playerOne.hasTurn = !this.playerOne.hasTurn;
      this.playerTwo.hasTurn = !this.playerTwo.hasTurn;
    },
    getPointsByColour(colour) {
      const colourPoints = {
        red: 1,
        yellow: 2,
        green: 3,
        brown: 4,
        blue: 5,
        pink: 6,
        black: 7,
      };
      return colourPoints[colour];
    },
    decrementRedBallCount() {
      if (this.redBall.quantity > 0) {
        this.redBall.quantity -= 1;
      }
    },
    completeMatch() {
      console.log('game over');
    },
  },
};
</script>

<style>
html, body, main {
  margin:0;
  padding:0;
  overflow: hidden;
}

h1, h2 {
  margin: 0;
  padding: 0;
}

.felt {
  background-image: url('./assets/green-felt.jpg');
  width: 100%;
  height: 100vh;
  margin: 0;
  padding: 0;
  position: relative;
}

.player-wrapper {
  padding: 10px 25px;
  -webkit-box-shadow:inset 0px 0px 0px 10px #f00;
    -moz-box-shadow:inset 0px 0px 0px 10px #f00;
    box-shadow:inset 0px 0px 0px 1px ivory;
}


.player-info {
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  color: #F5F5F5;
  border-bottom: 1px solid #FFFFF0;
}

.player-name, .player-score {
  padding: 0 10px 0 10px;
}

.player-history {
  padding: 5px 0;
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;
  flex-wrap: wrap;
}

.player-turn {
  background: #ccc2a24d;
}

.ball {
  max-height: 60px;
  max-width: 60px;
  opacity: 0.5;
  pointer-events: none;
}

.on-ball {
  opacity: 1;
  pointer-events: all;
}

.history-ball {
  width: 20px;
  height: 20px;
}

.red-ball {
  max-width: 80px;
  max-height: 80px;
  margin: 0 5px 80px 5px;
}

.ball-container {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  padding: 25px 5%;
  position:absolute;
  bottom:0;
  width:100%;
  height:40%;
}

.left-side {
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  margin: 0 auto;
  width: 33%;
}

.red-ball-container {
  display: flex;
  flex-direction: row;
  justify-content: center;
}

.red-ball-counter {
  position: absolute;
  padding-top: 20px;
  color: white;
  font-size: 34px;
  font-weight: bold;
  letter-spacing: 1px;
  font-family: Arial, Helvetica, sans-serif;
}

.action-buttons {
  bottom: 0;
  position: absolute;
  width: 100%;
  background-color: #2B1E16; 
}

.buttons {
  display: flex;
  flex-direction: row;
  color: #fffff0;
}

.btn-foul, .btn-undo {
  width: 25%;
  text-align: center;
  padding: 15px;
  border: 1px solid grey;
}

.btn-switch {
  width: 50%;
  padding: 15px;
  text-align: center;
  border: 1px solid grey;
}

.colour-triangle {
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  width: 66%;
  margin: 0 20px 80px 20px;
}

.top-row, .middle-row, .bottom-row {
  display: flex;
  flex-direction: row;
  justify-content: center;
  margin: 0 auto;
}

.noselect {
  -webkit-touch-callout: none; /* iOS Safari */
    -webkit-user-select: none; /* Safari */
     -khtml-user-select: none; /* Konqueror HTML */
       -moz-user-select: none; /* Firefox */
        -ms-user-select: none; /* Internet Explorer/Edge */
            user-select: none; /* Non-prefixed version, currently
                                  supported by Chrome and Opera */
}

.pointer {
  cursor: pointer;
}

.foulshot {
  color: red;
  font-weight: bold;
  font-size: 16px;
  text-align: center;
  background-color:ivory;
  border-radius: 100%;
  width: 19px;
  height: 18px;
  margin: 0 1px 4px 1px;
  display: inline-block;
}

</style>