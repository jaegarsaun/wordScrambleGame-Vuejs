<script>
import { _shuffleSelf } from 'lodash'
const words = [
  "Abstraction",
  "Adjudicate",
  "Adversary",
  "Aggregate",
  "Amplitude",
  "Ancestral",
  "Annihilate",
  "Antipathy",
  "Apparatus",
  "Apprehend",
  "Aquamarine",
  "Archiving",
  "Arrangement",
  "Articulate",
  "Assemblage",
  "Asseverate",
  "Assimilation",
  "Association",
  "Astringent",
  "Atmosphere",
  "Attenuation",
  "Authentication",
  "Automation",
  "Avaricious",
  "Backup",
  "Barometer",
  "Battalion",
  "Bibliography",
  "Biodegrade",
  "Blasphemy",
  "Blunderbuss",
  "Bombardment",
  "Buccaneer",
  "Bureaucrat",
  "Byzantine",
  "Calamitous",
  "Campanile",
  "Canonical",
  "Capricious",
  "Cartographer",
  "Cataclysm",
  "Cataract",
  "Catechism",
  "Cauterize",
  "Celestial",
  "Cellulose",
  "Centrifuge",
  "Cerebral",
  "Certitude",
  "Chameleon",
  "Charitable",
  "Chattel",
  "Checkered",
  "Chromosome",
  "Clandestine",
  "Clavichord",
  "Clemency",
  "Coalesce",
  "Coaxial",
  "Cognition",
  "Cohort",
  "Collation",
  "Collision",
  "Commandant",
  "Commemorate",
  "Commensurate",
  "Compendium",
  "Complacency",
  "Compliant",
  "Concatenate",
  "Condemnation",
  "Conducive",
  "Configuration",
  "Conglomerate",
  "Congruent",
  "Conjecture",
  "Consecrate",
  "Consonant",
  "Consolidate",
  "Consternation",
  "Contemplation",
  "Contingent",
  "Continuation",
  "Contraband",
  "Contrition",
  "Conundrum",
  "Convection",
  "Copious",
  "Corroborate",
  "Counterfeit",
  "Counterpoint",
  "Coverture",
  "Crenellate",
  "Crenellation",
  "Crescendo",
  "Culmination",
  "Curvaceous",
  "Cyanide",
  "Cyberspace",
  "Cyclopean"
];
export default {
  data() {
    return {
      userGuess: '',
      currentWord: '',
      unScrambledWord: '',
      userScore: 0,
    }
  },
  mounted(){
    
  },
  methods: {
    handelSubmit() {
      this.userGuess = this.userGuess.toLowerCase()
      this.unScrambledWord = this.unScrambledWord.toLowerCase()
      
      if (this.userGuess === this.unScrambledWord) {
        console.log('correct')
        this.userGuess = ''
        this.userScore++
        this.wordStart();
      } else {
        console.log('incorrect')
        this.userGuess= 'Incorrect!'
      }
      
    },

    clearSubmit(){
      this.userGuess = ''
    },
    wordStart(){
      this.unScrambledWord = words[Math.floor(Math.random() * words.length)]
      //Scramble the word
      let stringArray = this.unScrambledWord.split('')
      stringArray.sort(() => Math.random() - 0.5)
      this.userGuess = ''
      this.currentWord = stringArray.join('');

    },
  }
}
</script>

<template>
  <section class="content">
    <div class="bubble"></div>
    <div class="sec sec1">
      <div class="card">
        <p class="scrambled">{{ currentWord }}</p>
        <p class="userGuess">{{ userGuess }}</p>
      </div>
      <div class="card2"></div>
    </div>
    <div class="sec2">
      <form @submit="handelSubmit()">
        <input type="text" placeholder="Input here" v-model="userGuess" />
        <div class="buttons">
          <button type="button" @click="handelSubmit();">Submit</button>
          <button type="button" @click="wordStart();">Start</button>
        </div>

          <p class="score-title">Your Score: <span>{{ userScore }}</span></p>
        
      </form>
    </div>
  </section>
</template>

<style scoped>
template {
  background-color: red;
}
</style>
