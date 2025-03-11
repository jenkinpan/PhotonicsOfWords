<script setup>
import { ref } from "vue";

const words = ref([
  {
    word: "trousers",
    phonetic: "/ˈtraʊzərz/",
    audio: "trousers.mp3",
    chinese: "裤子（复数）",
  },
  { word: "suit", phonetic: "/suːt/", audio: "suit.mp3", chinese: "西装" },
  { word: "shirt", phonetic: "/ʃɜːrt/", audio: "shirt.mp3", chinese: "衬衫" },
  { word: "pants", phonetic: "/pænts/", audio: "pants.mp3", chinese: "裤子" },
  {
    word: "jacket",
    phonetic: "/ˈdʒækɪt/",
    audio: "jacket.mp3",
    chinese: "夹克",
  },
  { word: "dress", phonetic: "/dres/", audio: "dress.mp3", chinese: "连衣裙" },
  {
    word: "dresses",
    phonetic: "/ˈdresɪz/",
    audio: "dresses.mp3",
    chinese: "连衣裙（复数）",
  },
  { word: "near", phonetic: "/nɪr/", audio: "near.mp3", chinese: "附近" },
  {
    word: "newspaper",
    phonetic: "/ˈnjuːzpeɪpər/",
    audio: "newspaper.mp3",
    chinese: "报纸",
  },
  {
    word: "pencil",
    phonetic: "/ˈpensl/",
    audio: "pencil.mp3",
    chinese: "铅笔",
  },
  {
    word: "knives",
    phonetic: "/naɪvz/",
    audio: "knives.mp3",
    chinese: "小刀（复数）",
  },
  {
    word: "boxes",
    phonetic: "/ˈbɒksɪz/",
    audio: "boxes.mp3",
    chinese: "盒子（复数）",
  },
  {
    word: "watches",
    phonetic: "/ˈwɒtʃɪz/",
    audio: "watches.mp3",
    chinese: "手表（复数）",
  },
  {
    word: "armchair",
    phonetic: "/ˈɑːmˌtʃeər/",
    audio: "armchair.mp3",
    chinese: "扶手椅",
  },
]);

const playAudio = (word) => {
  speechSynthesis.cancel();
  const utterance = new SpeechSynthesisUtterance(word);
  utterance.lang = "en-US";
  speechSynthesis.speak(utterance);
};
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

<style src="./App.css" scoped></style>
