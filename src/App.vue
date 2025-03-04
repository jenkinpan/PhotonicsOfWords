<script setup>
import { ref } from 'vue'

const words = ref([
  { word: 'trousers', phonetic: '/ˈtraʊzərz/', audio: 'trousers.mp3', chinese: '裤子（复数）' },
  { word: 'suit', phonetic: '/suːt/', audio: 'suit.mp3', chinese: '西装' },
  { word: 'shirt', phonetic: '/ʃɜːrt/', audio: 'shirt.mp3', chinese: '衬衫' },
  { word: 'pants', phonetic: '/pænts/', audio: 'pants.mp3', chinese: '裤子' },
  { word: 'jacket', phonetic: '/ˈdʒækɪt/', audio: 'jacket.mp3', chinese: '夹克' },
  { word: 'dress', phonetic: '/dres/', audio: 'dress.mp3', chinese: '连衣裙' },
  { word: 'dresses', phonetic: '/ˈdresɪz/', audio: 'dresses.mp3', chinese: '连衣裙（复数）' },
  { word: 'near', phonetic: '/nɪr/', audio: 'near.mp3', chinese: '附近' },
  { word: 'newspaper', phonetic: '/ˈnjuːzpeɪpər/', audio: 'newspaper.mp3', chinese: '报纸' },
  { word: 'pencil', phonetic: '/ˈpensl/', audio: 'pencil.mp3', chinese: '铅笔' },
  { word: 'knives', phonetic: '/naɪvz/', audio: 'knives.mp3', chinese: '小刀（复数）' },
  { word: 'boxes', phonetic: '/ˈbɒksɪz/', audio: 'boxes.mp3', chinese: '盒子（复数）' },
  { word: 'watches', phonetic: '/ˈwɒtʃɪz/', audio: 'watches.mp3', chinese: '手表（复数）' },
  { word: 'armchair', phonetic: '/ˈɑːmˌtʃeər/', audio: 'armchair.mp3', chinese: '扶手椅' }
])

const playAudio = (word) => {
  speechSynthesis.cancel()
  const utterance = new SpeechSynthesisUtterance(word)
  utterance.lang = 'en-US'
  speechSynthesis.speak(utterance)
}
</script>

<template>
  <div class="container">
    <h1>第二次课相关单词</h1>
    <div v-for="(item, index) in words" :key="index" class="word-item">
      <div class="word-phonetic">
        <div class="word">{{ item.word }}</div>
        <div class="phonetic">{{ item.phonetic }}</div>
      </div>
      <div class="chinese">{{ item.chinese }}</div>
      <button @click="playAudio(item.word)">播放发音</button>
    </div>
  </div>
</template>

<style scoped>
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 1rem;
  margin-top: 80px;
}

h1 {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  text-align: center;
  font-weight: bold;
  background-color: white;
  padding: 1rem;
  z-index: 1000;
}

.word-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 1rem;
  border: 1px solid #ddd;
  border-radius: 8px;
  text-align: center;
}

.word {
  font-size: 1.2rem;
  font-weight: bold;
  margin-right: 1rem;
}

.phonetic {
  font-style: italic;
  margin-right: 1rem;
}

.word-phonetic {
  display: flex;
  align-items: center;
  margin-bottom: 0.5rem;
}

.chinese {
  margin-bottom: 0.5rem;
  color: #666;
}

button {
  padding: 0.5rem 1rem;
  background-color: #646cff;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #535bf2;
}

@media (max-width: 768px) {
  .container {
    padding: 1rem;
    grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  }
  .word-item {
    padding: 0.8rem;
  }
  button {
    width: 100%;
    margin-top: 0.5rem;
  }
}

@media (max-width: 480px) {
  .container {
    grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
  }
  .word {
    font-size: 1rem;
  }
  .phonetic {
    font-size: 0.9rem;
  }
  button {
    padding: 0.4rem 0.8rem;
    font-size: 0.9rem;
  }
}
</style>
