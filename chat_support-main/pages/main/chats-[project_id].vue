<template>
  <main class="lg:pl-72">
    <div class="xl:pl-96">
      <div class="px-4 py-10 sm:px-6 lg:px-8 lg:py-6">
        <!-- Mobile Chat List (visible only on small screens) -->
        <div class="lg:hidden mb-6">
          <ChatList
            :chats="chats"
            :selected-chat-id="selectedChat?.id"
            @select-chat="selectChat"
          />
        </div>

        <!-- Chat Window -->
        <div v-if="selectedChat && !isMobile" class="lg:block">
          <ChatWindow
            :initial-messages="currentMessages"
            @new-message="handleNewMessage"
            ref="chatWindow"
          />
        </div>

        <!-- No Chat Selected Message (shown on mobile when no chat is selected) -->
        <div v-if="!selectedChat && isMobile" class="flex items-center justify-center h-[calc(100vh-16rem)] text-gray-500">
          <p>Select a chat to start messaging</p>
        </div>
      </div>
    </div>
  </main>

  <!-- Desktop Chat List (hidden on small screens) -->
  <aside class="fixed inset-y-0 left-72 hidden w-96 overflow-y-auto border-r border-gray-200 px-4 py-6 sm:px-6 lg:px-8 xl:block">
    <ChatList
      :chats="chats"
      :selected-chat-id="selectedChat?.id"
      @select-chat="selectChat"
    />
  </aside>
</template>

<script setup>
import { ref, computed, onMounted } from 'vue'
import { Dialog, DialogPanel, TransitionChild, TransitionRoot } from '@headlessui/vue'
import {
  Bars3Icon,
  CalendarIcon,
  ChartPieIcon,
  DocumentDuplicateIcon,
  FolderIcon,
  HomeIcon,
  UsersIcon,
  XMarkIcon,
} from '@heroicons/vue/24/outline'
import ChatWindow from '~/components/ChatWindow.vue'
import ChatList from '~/components/ChatList.vue'

const navigation = [
  { name: 'Dashboard', href: '#', icon: HomeIcon, current: true },
  { name: 'Team', href: '#', icon: UsersIcon, current: false },
  { name: 'Projects', href: '#', icon: FolderIcon, current: false },
  { name: 'Calendar', href: '#', icon: CalendarIcon, current: false },
  { name: 'Documents', href: '#', icon: DocumentDuplicateIcon, current: false },
  { name: 'Reports', href: '#', icon: ChartPieIcon, current: false },
]
const teams = [
  { id: 1, name: 'Heroicons', href: '#', initial: 'H', current: false },
  { id: 2, name: 'Tailwind Labs', href: '#', initial: 'T', current: false },
  { id: 3, name: 'Workcation', href: '#', initial: 'W', current: false },
]

const sidebarOpen = ref(false)
const chatWindow = ref(null)
const currentMessages = ref([])
const selectedChat = ref(null)
const isMobile = ref(false)

const chats = ref([
  {
    id: 1,
    name: 'John Doe',
    initial: 'JD',
    lastMessage: 'I need help with my account settings',
    lastMessageTime: '10:30 AM',
    unread: true
  },
  {
    id: 2,
    name: 'Sarah Smith',
    initial: 'SS',
    lastMessage: 'Thank you for your help!',
    lastMessageTime: 'Yesterday',
    unread: false
  },
  {
    id: 3,
    name: 'Mike Johnson',
    initial: 'MJ',
    lastMessage: 'Can you explain the pricing?',
    lastMessageTime: '2 days ago',
    unread: false
  },
  {
    id: 4,
    name: 'Emily Brown',
    initial: 'EB',
    lastMessage: 'The new feature is working great!',
    lastMessageTime: 'Last week',
    unread: false
  }
])

const selectChat = (chat) => {
  selectedChat.value = chat
  // Here you would typically load the chat messages for the selected conversation
  currentMessages.value = [
    {
      content: `Hello! This is the conversation with ${chat.name}. How can I help you today?`,
      isUser: false,
      timestamp: '10:00 AM'
    }
  ]
}

const handleNewMessage = (message) => {
  // Here you would typically send the message to your backend
  // For now, we'll just simulate a response
  setTimeout(() => {
    chatWindow.value?.addMessage({
      content: 'I understand your message. How can I help you further?',
      isUser: false,
      timestamp: new Date().toLocaleTimeString([], { hour: '2-digit', minute: '2-digit' })
    })
  }, 1000)
}

onMounted(() => {
  // Check if we're on mobile
  const checkMobile = () => {
    isMobile.value = window.innerWidth < 1024 // lg breakpoint
  }
  
  // Initial check
  checkMobile()
  
  // Add resize listener
  window.addEventListener('resize', checkMobile)
  
  // Initialize with the first chat selected
  if (chats.value.length > 0) {
    selectChat(chats.value[0])
  }
})
</script>