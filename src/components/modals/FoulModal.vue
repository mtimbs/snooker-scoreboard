<template>
    <div v-show="displayModal"
         @click.self="dismissModal"
         class="modal-outer">
        <div class="modal-inner">
            <div class="border-2 border-brand-light p-1 border-dashed">
                <div class="text-white bg-brand rounded-lg">
                    <p class="px-6 py-6">Select Foul Points</p>
                </div>
                <div>
                  <button>4</button>
                  <button>5</button>
                  <button>6</button>
                  <button>7</button>
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
  background-color: black;
  border-radius: .25rem;
  box-shadow: 0 2px 4px 0 rgba(0,0,0,0.10);
  padding-top: 25px;
  margin: 50px;
  width: 100%;
  text-align: center;
  color: white;
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