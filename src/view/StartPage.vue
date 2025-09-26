<script setup lang="ts">
import { type Language } from '../classes/basics'
import * as text from './elements/text.json'
import { extractTextFromJson } from './basic'
const passwordValue: string = ''
let voterID: string = ''
const props = defineProps<{
  language: Language | undefined
  voterId: string
}>()
</script>

<template>
  <div class="start">
    <div class="explanation">{{ extractTextFromJson(text.login.textID, props.language) }}</div>
    <h4>{{ extractTextFromJson(text.login.voterId, props.language) }}</h4>
    <form @submit.prevent="$emit('login', passwordValue, voterID)">
      <div class="password">
        <input class="input" maxlength="8" autocomplete="off" v-model="voterID"/>
      </div>
      <div class="explanation">{{ extractTextFromJson(text.login.textPW, props.language) }}</div>
      <h4>{{ extractTextFromJson(text.login.loginReq, props.language) }}</h4>
      <div class="password">
        <input id="enter" class="input" maxlength="6" autocomplete="new-password one-time-code"
          :type="passwordFieldType" v-model="passwordValue">
        <i :class="togglerIcon" id="eye" @click="switchVisibility"></i>
      </div>
      <!-- <div class="explanation">{{ extractTextFromJson(text.login.explanation, props.language) }}</div> -->
      <button class="login" v-on:click="$emit('login', passwordValue, voterID)">
        {{ extractTextFromJson(text.login.loginButton, props.language) }}
      </button>
    </form>
  </div>
</template>

<script lang="ts">
export default {
  data() {
    return {
      password: '',
      passwordFieldType: 'password',
      togglerIcon: 'fa fa-eye'
    }
  },
  methods: {
    switchVisibility() {
      this.passwordFieldType = this.passwordFieldType === 'password' ? 'text' : 'password'
      this.togglerIcon = this.togglerIcon === 'fa fa-eye' ? 'fa fa-eye-slash' : 'fa fa-eye'
    }
  }
}
</script>

<style scoped>
.start {
  max-width: 400pt;
  margin: auto;
  text-align: center;
  font-size: 12pt;
}

.explanation {
  text-align: justify;
}

.voterid {
  margin-top: -4%;
  margin-bottom: -2%;
  margin-left: 24.5%;
  padding-left: 0.75%;
  border: 0.1px solid #bbb;
  width: 50%;
  background-color: #f8f8f8;
}

.password {
  margin-top: -4%;
  margin-bottom: 4%;
}

.input {
  width: 100%;
  font-size: 12pt;
  border-radius: 5pt;
  border-width: 1px;
  padding: 5pt;
  box-sizing: border-box;
}

#eye {
  position: absolute;
  margin-top: 7.5pt;
  margin-left: -20pt;
  cursor: pointer;
  color: #404040;
  size: 12pt;
}

.login {
  width: 100%;
  padding-top: 5pt;
  padding-bottom: 5pt;
  font-weight: bold;
  margin-top: 4%;
  font-size: 12pt;
  background-color: #4664aa;
  color:white;
  border-radius: 5pt;
  border: 1px solid #4664aa;
}

h4 {
  text-align: left;
}
</style>
