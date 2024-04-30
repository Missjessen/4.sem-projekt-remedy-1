<template>
    <div>
      <input v-model="prompt" placeholder="Enter your prompt">
      <button @click="fetchResponse">Get Response</button>
      <p>Response: {{ response }}</p>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  import axios from 'axios';
  
  const prompt = ref('');
  const response = ref('');

 
 // const API_KEY = "sk-proj-2LiIWht9AZEFOsqSvV77T3BlbkFJf5yf0RQp00u1rsgmvZSA";

 // const axios = require('axios');
async function fetchGPTResponse() {
    const proxyUrl = 'https://cors-anywhere.herokuapp.com/';
    const targetUrl = 'https://api.openai.com/v1/models/gpt-4.0-turbo/completions';
    const params = {
        prompt: "What are the main benefits of using renewable energy sources?",
        max_tokens: 100
    };
    const headers = {
        'Authorization': `Bearer sk-proj-2LiIWht9AZEFOsqSvV77T3BlbkFJf5yf0RQp00u1rsgmvZSA`,
        'Content-Type': 'application/json'
    };

    try {
        const response = await axios.post(proxyUrl + targetUrl, params, { headers });
        console.log(response.data);
    } catch (error) {
        console.error('Error fetching response:', error);
    }
}

fetchGPTResponse();





// const fetchResponse = async () => {
//   const params = {
//     prompt: prompt.value,
//     max_tokens: 100
//   };

//   const headers = {
//     'Authorization': `Bearer ${API_KEY}`,  // Correctly formatted header
//     'Content-Type': 'application/json'
//   };

//   try {
//   const result = await axios.post('https://api.openai.com/v1/engines/text-davinci-002/completions', params, { headers });
//   response.value = result.data.choices[0].text;
// } catch (error) {
//   if (error.response && error.response.data.error) {
//     console.error('Error message:', error.response.data.error.message);
//   } else {
//     console.error('Error fetching response:', error);
//   }
// }

// };

  </script>
  