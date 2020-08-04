<template>
  <div id="app">
    <nav class="mt-3">
      <div class="container has-text-centered">
        <h1 class="is-size-2">Card Counter</h1>
      </div>
    </nav>

    <section>
      <div class="container px-5">
        <div class="level is-mobile mt-4">
          <div class="level-left">
            <div class="level-item">
              <button class="button is-light is-normal" v-on:click="reset">Reset</button>
            </div>
          </div>

          <div class="level-right">
            <div class="level-item">
              <span class="is-size-4">Decks</span>
            </div>
            <div class="level-item">
              <div class="select">
                <select v-model="deck" v-on:change="reset" id="deck-selecter">
                  <option v-for="n in 8" :key="n">{{ n }}</option>
                </select>
              </div>
            </div>
          </div>
        </div>

        <Display
          v-bind:remaining="remaining"
          v-bind:count="trueCount"
        />

        <CountButton v-on:click="up"   v-bind:disabled="isUncountable">10, J, Q, K, A</CountButton>
        <CountButton v-on:click="draw" v-bind:disabled="isUncountable">7, 8, 9</CountButton>
        <CountButton v-on:click="down" v-bind:disabled="isUncountable">2, 3, 4, 5, 6</CountButton>
      </div>
    </section>

  </div>
</template>

<script>
import CountButton from './components/CountButton';
import Display from './components/Display';

const DECK_OF_CARDS = 52;

export default {
  name: 'App',
  components: {
    CountButton,
    Display
  },
  data: function () {
    return {
      count: 0,
      deck: 1,
      remaining: DECK_OF_CARDS
    };
  },
  methods: {
    reset: function () {
      this.count = 0;
      this.remaining = this.deck * DECK_OF_CARDS;
    },
    up: function () {
      this.remaining--;
      this.count++;
    },
    down: function () {
      this.remaining--;
      this.count--;
    },
    draw: function () {
      this.remaining--;
    }
  },
  computed: {
    trueCount: function () {
      if (this.remaining <= 0) {
        return '-';
      }
      return (this.count / Math.ceil(this.remaining / DECK_OF_CARDS)).toFixed(2);
    },
    isUncountable: function () {
      return this.remaining <= 0;
    }
  }
}
</script>
