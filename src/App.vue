<template>
  <div id="app">
    <main class="felt noselect"> 
      <div class="player-wrapper">
        <div class="player-container">
          <div class="player-info">
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
          <div class="player-info">
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
              <red-ball class="red-ball pointer ball"/>
              <span class="red-ball-counter pointer">
                {{redBallCount}}
              </span>
            </div>
          </div>
        </div>
        <div class="colour-triangle">
          <div class="top-row">
            <black-ball class="pointer ball"/>
          </div>
          <div class="middle-row">
            <pink-ball class="pointer ball"/>
            <blue-ball class="pointer ball"/>
          </div>
          <div class="bottom-row">
            <yellow-ball class="pointer ball"/>
            <green-ball class="pointer ball"/>
            <brown-ball class="pointer ball"/>
          </div>
        </div>
      </div>
      <div class="action-buttons">
        <div class="buttons">
          <a class="pointer btn btn-foul">FOUL</a>
          <a class="pointer btn btn-undo">UNDO</a>
          <a class="pointer btn btn-switch">SWITCH PLAYER</a>
        </div>
      </div>
    </main>
  </div>
</template>

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
  background: black;
  -webkit-box-shadow:inset 0px 0px 0px 10px #f00;
    -moz-box-shadow:inset 0px 0px 0px 10px #f00;
    box-shadow:inset 0px 0px 0px 1px ivory;
}

.player-container {}

.player-info {
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  color: #F5F5F5;
  border-bottom: 1px solid #FFFFF0;
}

.player-history {
  padding: 5px 0;
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;
  flex-wrap: wrap;
}

.ball {
  max-height: 60px;
  max-width: 60px;
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
        template: '<red-ball class="history-ball"/>',
      },
      yellowBall: {
        quantity: 1,
        on: false,
        points: 2,
        template: '<yellow-ball class="history-ball"/>',
      },
      greenBall: {
        quantity: 1,
        on: false,
        points: 3,
        template: '<green-ball class="history-ball"/>',
      },
      brownBall: {
        quantity: 1,
        on: false,
        points: 4,
        template: '<brown-ball class="history-ball"/>',
      },
      blueBall: {
        quantity: 1,
        on: false,
        points: 5,
        template: '<blue-ball class="history-ball"/>',
      },
      pinkBall: {
        quantity: 1,
        on: false,
        points: 6,
        template: '<pink-ball class="history-ball"/>',
      },
      blackBall: {
        quantity: 1,
        on: false,
        points: 7,
        template: '<black-ball class="history-ball"/>',
      },
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
      if (colour === 'red' && this.redBallCount === 0) {
        return;
      }

      if (this.playerOne.hasTurn) {
        this.playerOne.shotHistory.push(this.newBall(colour));
      }

      if (this.playerTwo.hasTurn) {
        this.playerTwo.shotHistory.push(this.newBall(colour));
      }

      if (colour === 'red') {
        this.decrementRedBallCount();
      }
    },
    newBall(colour) {
      return {
        colour,
        points: this.getPointsByColour(colour),
      };
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
        this.redBall.quantity = this.redBall.quantity - 1;
      }
    },
  },
};
</script>