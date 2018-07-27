<template>
    <div v-show="displayModal"
         @click.self="$emit('dismiss')"
         class="modal-outer">
        <div class="modal-inner">
            <div class="border-2 border-brand-light p-1 border-dashed">
                <div class="foul-button-wrapper">
                  <button class="foul-button" @click="$emit('foul', 4)">4</button>
                  <button class="foul-button" @click="$emit('foul', 5)">5</button>
                  <button class="foul-button" @click="$emit('foul', 6)">6</button>
                  <button class="foul-button" @click="$emit('foul', 7)">7</button>
                </div>
            </div>
        </div>
    </div>
</template>

<style>
.modal-outer {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  z-index: 50;
  background: #00000096;
}

.modal-inner {
  background-color: rgba(0,0,0,0.90);
  border-radius: .25rem;
  box-shadow: 0 2px 4px 0 rgba(0,0,0,0.10);
  margin: 10%;
  width: 100%;
  text-align: center;
  color: white;
}

.foul-button {
  width: 85%;
  max-width: 4000px;
  margin: 10px 15px;
  padding: 15px;
  background-color: rgba(0,0,0,0.10);
  color: white;
  font-weight: bold;
  font-size: 1rem;
}

.foul-button-wrapper {
  margin: 30px 0;
}
</style>


<script>
export default {
  name: 'FoulModal',
  props: {
    displayModal: {
      type: Boolean,
      required: true,
    },
  },
  data() {
    return {
      foo: 'bar',
    };
  },
};
</script>