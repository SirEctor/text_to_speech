<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
</script>

<template>
  <div style="text-align: center; display:flex; flex-direction: column; height: 100vh; justify-content: center; align-items: center;"> 
    <h1 style="font-size:6.5em;">Text To Speech Converter</h1>
    <div style="display:flex;flex-direction:row;align-content:space-around;width:100%;justify-content:space-evenly">
      <h2 style="font-size:4em;">Text:</h2>
      <textarea style="width: 785px;height: 180px;" placeholder="Enter text here."></textarea>
    </div>
    
    <div style="display:flex;flex-direction:row;align-content:space-around;width:100%;justify-content:space-evenly;margin-top:20px;">
      <h2 style="font-size:4em;">Voices:</h2>
      <select>
        <option>Test Voice 1</option>
        <option>Test Voice 2</option>
      </select>
    </div>
    
    <button style="margin-top:20px;font-size:1em;">Generate</button>
  </div>
</template>

