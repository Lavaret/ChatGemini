<template>
  <div class="about" :class="{'content': content}">
    <h3>Consult with crystal ball</h3>
    <div class="button-nav">
      <input @keydown.enter="run"  class="prompt-input" v-model="prompt">
      <button @click="run">Run</button>
    </div>
    <div v-if="loading" class="loading"><EcosystemIcon class="loading-icon"/></div>
    <pre v-if="content" class="response">
      {{ content }}
    </pre>
  </div>
</template>

<script type="module" setup lang="ts">
import { ref } from 'vue';
import { GoogleGenerativeAI } from "@google/generative-ai";
import EcosystemIcon from '@/components/icons/IconEcosystem.vue'

const prompt = ref('Write a story about a magic backpack.')
const content = ref('')
const loading = ref(false)
// Fetch your API_KEY
const API_KEY = import.meta.env.VITE_GEMINI_API_KEY;
// Reminder: This should only be for local testing

const run = async () => {

  if (!prompt.value) {
    return
  }
  loading.value = true
  content.value = ''
  // Access your API key (see "Set up your API key" above)
  const genAI = new GoogleGenerativeAI(API_KEY);

  // The Gemini 1.5 models are versatile and work with most use cases
  const model = genAI.getGenerativeModel({ model: "gemini-1.5-flash"});

  const result = await model.generateContent(prompt.value);
  const response = await result.response;
  loading.value = false
  content.value = response.text();
  console.log(response);
}

</script>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: start;
    justify-content: center;
    padding: 3rem 0;
  }
}

.about.content {
  margin: auto;
}

.loading {
  height: 15rem;
  display: flex;
  justify-content: center;
  width: 100%;
  padding: 2rem;
}

.loading-icon {
  animation: rotate 3s linear 0s infinite;
}

@keyframes rotate {
  from {transform: rotate(0deg);}
  to {transform: rotate(-360deg);}
}

.prompt-input {
  background-color: transparent;
  color: var(--color-text);
  border-radius: 5px;
  width: 100%;
  padding: 1em;
  height: 100%;
  font-size: 1rem;
  border: 1px solid var(--color-text);
}

.response {
  width: 100%;
  min-height: 25%;
  border: 1px solid var(--color-border);
  padding: 1em;
  color: var(--color-text);
  white-space: break-spaces;
  max-height: 700px;
  overflow-y: scroll;
  scrollbar-width: none;
}

.button-nav {
  display: flex;
  justify-content: center;
  align-content: center;
  gap: 1em;
  width: 100%;
  padding: 1rem 0;
}

button {
  background-color: var(--gold);
  font-size: 1.2rem;
  color: black;
  border-style: solid;
  border-color: var(--color-border);
  padding: .5rem 1rem;
  border-radius: 5px;
}

button:hover {
  background-color: var(--gold-dark);
  cursor: pointer;
}
</style>
