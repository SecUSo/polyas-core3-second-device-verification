<script setup lang="ts">

const props = defineProps<{
    modelValue: boolean
}>()

const emit = defineEmits(['update:modelValue']);

const closeModal = () => {
  emit('update:modelValue', false);
};

</script>


<template>
    <div v-if="modelValue" class="modal" @click.self="closeModal">
        <div v-if="modelValue" class="modal-content">
            <span class="close-btn" @click="closeModal">&times;</span>
            <slot>
            </slot>
        </div>
    </div>
</template>
<style scoped>
.modal {
  position: fixed;
  z-index: 1000;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  overflow: auto;
  background-color: rgba(0, 0, 0, 0.5);
}

.modal-content {
  background-color: #fefefe;
  margin: 15% auto;
  padding: 20px;
  border: 1px solid #888;
  width: 80%;
  max-width: 500px;
  border-radius: 8px;
  position: relative;
}

.close-btn {
  color: #aaa;
  float: right;
  font-size: 28px;
  font-weight: bold;
  cursor: pointer;
}

.close-btn:hover,
.close-btn:focus {
  color: black;
}

</style>