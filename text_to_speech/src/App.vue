<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'

import { ref } from 'vue'

const generating = ref(true);
console.log(generating.value);
const theInputText = ref('');
const chosenVoice = ref('');

async function testFunc() {
  console.log(theInputText.value);
  console.log(chosenVoice.value);
  console.log(generating.value);
  generating.value = true;
  console.log(generating.value);
  try {
    generating.value = false;
    
    let resp = await fetch('https://api.streamelements.com/kappa/v2/speech?voice='+chosenVoice.value+'&text="' + theInputText.value +'"');
    let mp3 = await resp.blob();
    
    let blobUrl = URL.createObjectURL(mp3);
    document.getElementById('source').setAttribute('src', blobUrl);
    let audio = document.getElementById('audio');
    audio.pause();
    audio.load();
    audio.play();
    
  } catch(error){
    console.log(error);
  }
}
</script>

<template>
  <div style="text-align: center; display:flex; flex-direction: column; height: 100vh; justify-content: center; align-items: center;"> 
    <h1 style="font-size:6.5em;">Text To Speech Converter</h1>
    <div style="display:flex;flex-direction:row;align-content:space-around;width:100%;justify-content:space-evenly">
      <h2 style="font-size:4em;">Text:</h2>
      <textarea v-model="theInputText" style="width: 785px;height: 180px;" placeholder="Enter text here."></textarea>
    </div>
    
    <div style="display:flex;flex-direction:row;align-content:space-around;width:100%;justify-content:space-evenly;margin-top:20px;">
      <h2 style="font-size:4em;">Voices:</h2>
      <select v-model="chosenVoice">
        <option disabled value="">Please select one.</option>
        <option>Brian</option>
        <option>Ivy</option>
      </select>
    </div>
    
    <button @click="testFunc" style="margin-top:20px;font-size:3em;">Generate</button>
    <h1 v-if="generating">GENERATING RESULT HERE...</h1>
    <audio id="audio" controls="true" v-else>
        <source id="source" type="audio/wav">
    </audio>

  </div>
</template>
