<script setup lang="ts">
import { extractTextFromJson } from './basic'
import { type Language } from '../classes/basics'
import * as text from './elements/text.json'

const props = defineProps<{
  language: Language | undefined
}>()
</script>
<template>
    <div>

        <h2>{{ extractTextFromJson(text.successPage.successHeader, props.language) }}</h2>
        <p> {{ extractTextFromJson(text.successPage.successText, props.language) }} </p>

    </div>
</template>

<style scoped>

</style>