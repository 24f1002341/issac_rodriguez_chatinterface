<template>
  <div class="flex flex-col h-[calc(100vh-8rem)]">
    <!-- Chat Messages Area -->
    <div class="flex-1 overflow-y-auto mb-4 space-y-4">
      <div v-for="(message, index) in messages" :key="index" 
           :class="['flex', message.isUser ? 'justify-end' : 'justify-start']">
        <div :class="['max-w-[70%] rounded-lg px-4 py-2', 
                    message.isUser ? 'bg-indigo-600 text-white' : 'bg-gray-100 text-gray-900']">
          <p class="text-sm">{{ message.content }}</p>
          <span class="text-xs opacity-75">{{ message.timestamp }}</span>
        </div>
      </div>
    </div>

    <!-- Chat Input Area -->
    <div class="border-t border-gray-200 pt-4">
      <div class="flex space-x-3">
        <input
          v-model="newMessage"
          type="text"
          placeholder="Type your message..."
          class="flex-1 rounded-lg border border-gray-300 px-4 py-2 focus:border-indigo-500 focus:ring-indigo-500"
          @keyup.enter="sendMessage"
        />
        <button
          @click="sendMessage"
          class="inline-flex items-center rounded-lg bg-indigo-600 px-4 py-2 text-sm font-semibold text-white hover:bg-indigo-500 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2"
        >
          Send
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const props = defineProps({
  initialMessages: {
    type: Array,
    default: () => []
  }
})

const emit = defineEmits(['new-message'])

const messages = ref(props.initialMessages)
const newMessage = ref('')

const sendMessage = () => {
  if (newMessage.value.trim()) {
    const message = {
      content: newMessage.value,
      isUser: true,
      timestamp: new Date().toLocaleTimeString([], { hour: '2-digit', minute: '2-digit' })
    }
    messages.value.push(message)
    emit('new-message', message)
    newMessage.value = ''
  }
}

// Method to add a message (can be called from parent)
const addMessage = (message) => {
  messages.value.push(message)
}

// Expose methods to parent component
defineExpose({
  addMessage
})
</script> 