<template>
  <div id="app">
    <site-header/>
      <form v-show="playing" v-on:submit.prevent="manageGameplay">
        <label for="word1">Noun: </label>
        <input type="text" id="word1" v-model="userWords.word1" />
        <br>
        <label for="word2">Verb: </label>
        <input type="text" id="word2" v-model="userWords.word2"/>
        <br>
        <label for="word3">Adjective: </label>
        <input type="text" id="word3" v-model="userWords.word3"/>
        <br>
        <label for="word4">Noun: </label>
        <input type="text" id="word4" v-model="userWords.word4"/>
        <br>
        <label for="word5">Adjective: </label>
        <input type="text" id="word5" v-model="userWords.word5"/>
        <br>
        <button type="submit">Generate</button>
      </form>
      <div v-show="!playing">
        <p>
          Perhaps it may be that my mind is wrought
          <br>To a <strong>{{ userWords.word1 }}</strong> by the moonbeam that hangs o’er,
          <br>But I will half <strong>{{ userWords.word2 }}</strong> that wild light fraught
          <br>With more of sovereignty than ancient lore
          <br>Hath ever told—or is it of a thought
          <br>The <strong>{{ userWords.word3 }}</strong> essence, and no more
          <br>That with a quickening spell doth o’er us pass
          <br>As <strong>{{ userWords.word4 }}</strong> of the night-time, o’er the <strong>{{ userWords.word5 }}</strong> grass?
        </p>
        <button v-on:click="manageGameplay">Play Again</button>
      </div>
    <site-footer/>
  </div>
</template>

<script>
import SiteHeader from './components/SiteHeader';
import SiteFooter from './components/SiteFooter';

export default {
  name: 'App',
  components: {
    SiteHeader,
    SiteFooter
  },
  data() {
    return {
      userWords: {
        word1: "",
        word2: "",
        word3: "",
        word4: "",
        word5: ""
      },
      playing: true
    }
  },
  methods: {
    manageGameplay() {
      if(this.playing === true) {
        this.playing = false;
      } else {
        this.playing = true;
        this.userWords.word1 = "";
        this.userWords.word2 = "";
        this.userWords.word3 = "";
        this.userWords.word4 = "";
        this.userWords.word5 = "";
      }
    }
  }
}
</script>

<style>
  strong {
    font-weight: 900;
    text-decoration: underline;
  }
</style>
