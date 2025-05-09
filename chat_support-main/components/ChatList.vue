<template>
  <div class="flex flex-col h-full">
    <div class="mb-4">
      <h2 class="text-lg font-semibold text-gray-900">Conversations</h2>
    </div>
    
    <!-- Search Input -->
    <div class="mb-4">
      <div class="relative">
        <input
          type="text"
          v-model="searchQuery"
          placeholder="Search conversations..."
          class="w-full rounded-lg border border-gray-300 pl-10 pr-4 py-2 focus:border-indigo-500 focus:ring-indigo-500"
        />
        <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
          <svg class="h-5 w-5 text-gray-400" viewBox="0 0 20 20" fill="currentColor">
            <path fill-rule="evenodd" d="M8 4a4 4 0 100 8 4 4 0 000-8zM2 8a6 6 0 1110.89 3.476l4.817 4.817a1 1 0 01-1.414 1.414l-4.816-4.816A6 6 0 012 8z" clip-rule="evenodd" />
          </svg>
        </div>
      </div>
    </div>

    <!-- Chat List -->
    <div class="flex-1 overflow-y-auto space-y-1">
      <button
        v-for="chat in filteredChats"
        :key="chat.id"
        @click="selectChat(chat)"
        :class="[
          'w-full flex items-center gap-x-3 rounded-lg px-3 py-2 text-sm leading-6',
          selectedChatId === chat.id
            ? 'bg-gray-50 text-indigo-600'
            : 'text-gray-700 hover:bg-gray-50'
        ]"
      >
        <div class="flex h-8 w-8 shrink-0 items-center justify-center rounded-lg bg-gray-50 text-[0.625rem] font-medium text-gray-600">
          {{ chat.initial }}
        </div>
        <div class="flex min-w-0 flex-1 flex-col">
          <div class="flex items-center justify-between gap-x-2">
            <p class="truncate font-medium">{{ chat.name }}</p>
            <p class="text-xs text-gray-500">{{ chat.lastMessageTime }}</p>
          </div>
          <p class="truncate text-xs text-gray-500">{{ chat.lastMessage }}</p>
        </div>
      </button>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const props = defineProps({
  chats: {
    type: Array,
    required: true
  },
  selectedChatId: {
    type: Number,
    default: null
  }
})

const emit = defineEmits(['select-chat'])

const searchQuery = ref('')

const filteredChats = computed(() => {
  if (!searchQuery.value) return props.chats
  const query = searchQuery.value.toLowerCase()
  return props.chats.filter(chat => 
    chat.name.toLowerCase().includes(query) || 
    chat.lastMessage.toLowerCase().includes(query)
  )
})

const selectChat = (chat) => {
  emit('select-chat', chat)
}
</script> 