<template>
  <div id="app">
    <main class="felt"> 
      <div class="ball-container">
        <div class="left-side">
          <div>
            <div @click="decrementRedBallCount" class="red-ball-container">
              <red-ball class="red-ball"/>
              <span class="red-ball-counter" :class="{'pad-left' : redBallCountPadLeft}">{{redBallCount}}</span>
            </div>
            <div class="action-buttons">
              <button>FOUL</button>
              <button>UNDO</button>
            </div>
          </div>
        </div>
        <div class="colour-triangle">
          <div class="top-row">
            <black-ball/>
          </div>
          <div class="middle-row">
            <pink-ball/>
            <blue-ball/>
          </div>
          <div class="bottom-row">
            <yellow-ball/>
            <green-ball/>
            <brown-ball/>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<style>
html, body {
  margin:0;
  padding:0;
  overflow: hidden;
}

.felt {
  background-image: url('./assets/green-felt.jpg');
  width: 100%;
  height: 100vh;
  margin: 0;
  padding: 0;
  position: relative;
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
  justify-content: center;
  margin: auto;
  width: 33%;
}

.red-ball-container {
  position: relative;
}

.red-ball {
  margin-left: 15%;
}

.red-ball-counter {
  position: absolute;
  top: 35%;
  left: 40%;
  color: white;
  font-size: 36px;
  font-weight: bold;
  letter-spacing: 1px;
  font-family: Arial, Helvetica, sans-serif;
}

.red-ball-counter.pad-left {
  left: 45%!important;
}

.action-buttons {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  padding: 15px;
}

.action-buttons > button {
  background-colour: white;
  colour: grey;
  font-weight: semibold;
  padding: 15px 25px;
  margin: 0 5px;
}

.colour-triangle {
  display: flex;
  flex-direction: column;
  width: 66%;
}

.top-row, .middle-row, .bottom-row {
  flex-direction: row;
  justify-content: center;
  margin: auto;
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
    };
  },
  computed: {
    redBallCount() {
      return this.redBall.quantity;
    },
    redBallCountPadLeft() {
      return this.redBallCount < 10;
    },
  },
  methods: {
    decrementRedBallCount() {
      if (this.redBall.quantity > 0) {
        this.redBall.quantity = this.redBall.quantity - 1;
      }
    },
  },
};
</script>