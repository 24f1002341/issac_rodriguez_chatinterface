<template>

<main class="lg:pl-72">
          <h1 class="sr-only">Account Settings</h1>
  
          <header class="border-b border-gray-200">
            <!-- Secondary navigation -->
            <nav class="flex overflow-x-auto py-4">
              <ul role="list" class="flex min-w-full flex-none gap-x-6 px-4 text-sm/6 font-semibold text-gray-500 sm:px-6 lg:px-8">
                <li v-for="item in secondaryNavigation" :key="item.name">
                  <a :href="item.href" :class="item.current ? 'text-indigo-600' : ''">{{ item.name }}</a>
                </li>
              </ul>
            </nav>
          </header>
  
          <!-- Settings forms -->
          <div class="divide-y divide-gray-200">
            <div class="grid max-w-7xl grid-cols-1 gap-x-8 gap-y-10 px-4 py-16 sm:px-6 md:grid-cols-3 lg:px-8">
              <div>
                <h2 class="text-base/7 font-semibold text-gray-900">Personal Information</h2>
                <p class="mt-1 text-sm/6 text-gray-500">Use a permanent address where you can receive mail.</p>
              </div>
  
              <form class="md:col-span-2">
                <div class="grid grid-cols-1 gap-x-6 gap-y-8 sm:max-w-xl sm:grid-cols-6">
                  <div class="col-span-full flex items-center gap-x-8">
                    <img src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="" class="size-24 flex-none rounded-lg bg-gray-50 object-cover" />
                    <div>
                      <button type="button" class="rounded-md bg-white px-3 py-2 text-sm font-semibold text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 hover:bg-gray-50">Change avatar</button>
                      <p class="mt-2 text-xs/5 text-gray-500">JPG, GIF or PNG. 1MB max.</p>
                    </div>
                  </div>
  
                  <div class="sm:col-span-3">
                    <label for="first-name" class="block text-sm/6 font-medium text-gray-900">First name</label>
                    <div class="mt-2">
                      <input type="text" name="first-name" id="first-name" autocomplete="given-name" class="block w-full rounded-md border-0 px-3 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm/6" />
                    </div>
                  </div>
  
                  <div class="sm:col-span-3">
                    <label for="last-name" class="block text-sm/6 font-medium text-gray-900">Last name</label>
                    <div class="mt-2">
                      <input type="text" name="last-name" id="last-name" autocomplete="family-name" class="block w-full rounded-md border-0 px-3 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm/6" />
                    </div>
                  </div>
  
                  <div class="col-span-full">
                    <label for="email" class="block text-sm/6 font-medium text-gray-900">Email address</label>
                    <div class="mt-2">
                      <input id="email" name="email" type="email" autocomplete="email" class="block w-full rounded-md border-0 px-3 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm/6" />
                    </div>
                  </div>
  
                  <div class="col-span-full">
                    <label for="username" class="block text-sm/6 font-medium text-gray-900">Username</label>
                    <div class="mt-2">
                      <div class="flex items-center rounded-md border-0 px-3 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 focus-within:ring-2 focus-within:ring-inset focus-within:ring-indigo-600">
                        <div class="shrink-0 text-base text-gray-500 select-none sm:text-sm/6">example.com/</div>
                        <input type="text" name="username" id="username" class="block min-w-0 grow border-0 bg-transparent py-1.5 pl-1 text-gray-900 placeholder:text-gray-400 focus:outline-none focus:ring-0 sm:text-sm/6" placeholder="janesmith" />
                      </div>
                    </div>
                  </div>
  
                  <div class="col-span-full">
                    <label for="timezone" class="block text-sm/6 font-medium text-gray-900">Timezone</label>
                    <div class="mt-2 grid grid-cols-1">
                      <select id="timezone" name="timezone" class="col-start-1 row-start-1 w-full appearance-none rounded-md border-0 px-3 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm/6">
                        <option>Pacific Standard Time</option>
                        <option>Eastern Standard Time</option>
                        <option>Greenwich Mean Time</option>
                      </select>
                      <ChevronDownIcon class="pointer-events-none col-start-1 row-start-1 mr-2 size-5 self-center justify-self-end text-gray-400 sm:size-4" aria-hidden="true" />
                    </div>
                  </div>
                </div>
  
                <div class="mt-8 flex">
                  <button type="submit" class="rounded-md bg-indigo-600 px-3 py-2 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600">Save</button>
                </div>
              </form>
            </div>
  
            <div class="grid max-w-7xl grid-cols-1 gap-x-8 gap-y-10 px-4 py-16 sm:px-6 md:grid-cols-3 lg:px-8">
              <div>
                <h2 class="text-base/7 font-semibold text-gray-900">Change password</h2>
                <p class="mt-1 text-sm/6 text-gray-500">Update your password associated with your account.</p>
              </div>
  
              <form class="md:col-span-2">
                <div class="grid grid-cols-1 gap-x-6 gap-y-8 sm:max-w-xl sm:grid-cols-6">
                  <div class="col-span-full">
                    <label for="current-password" class="block text-sm/6 font-medium text-gray-900">Current password</label>
                    <div class="mt-2">
                      <input id="current-password" name="current_password" type="password" autocomplete="current-password" class="block w-full rounded-md border-0 px-3 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm/6" />
                    </div>
                  </div>
  
                  <div class="col-span-full">
                    <label for="new-password" class="block text-sm/6 font-medium text-gray-900">New password</label>
                    <div class="mt-2">
                      <input id="new-password" name="new_password" type="password" autocomplete="new-password" class="block w-full rounded-md border-0 px-3 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm/6" />
                    </div>
                  </div>
  
                  <div class="col-span-full">
                    <label for="confirm-password" class="block text-sm/6 font-medium text-gray-900">Confirm password</label>
                    <div class="mt-2">
                      <input id="confirm-password" name="confirm_password" type="password" autocomplete="new-password" class="block w-full rounded-md border-0 px-3 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm/6" />
                    </div>
                  </div>
                </div>
  
                <div class="mt-8 flex">
                  <button type="submit" class="rounded-md bg-indigo-600 px-3 py-2 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600">Save</button>
                </div>
              </form>
            </div>
  
            <div class="grid max-w-7xl grid-cols-1 gap-x-8 gap-y-10 px-4 py-16 sm:px-6 md:grid-cols-3 lg:px-8">
              <div>
                <h2 class="text-base/7 font-semibold text-gray-900">Log out other sessions</h2>
                <p class="mt-1 text-sm/6 text-gray-500">Please enter your password to confirm you would like to log out of your other sessions across all of your devices.</p>
              </div>
  
              <form class="md:col-span-2">
                <div class="grid grid-cols-1 gap-x-6 gap-y-8 sm:max-w-xl sm:grid-cols-6">
                  <div class="col-span-full">
                    <label for="logout-password" class="block text-sm/6 font-medium text-gray-900">Your password</label>
                    <div class="mt-2">
                      <input id="logout-password" name="password" type="password" autocomplete="current-password" class="block w-full rounded-md border-0 px-3 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm/6" />
                    </div>
                  </div>
                </div>
  
                <div class="mt-8 flex">
                  <button type="submit" class="rounded-md bg-indigo-600 px-3 py-2 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600">Log out other sessions</button>
                </div>
              </form>
            </div>
  
            <div class="grid max-w-7xl grid-cols-1 gap-x-8 gap-y-10 px-4 py-16 sm:px-6 md:grid-cols-3 lg:px-8">
              <div>
                <h2 class="text-base/7 font-semibold text-gray-900">Delete account</h2>
                <p class="mt-1 text-sm/6 text-gray-500">No longer want to use our service? You can delete your account here. This action is not reversible. All information related to this account will be deleted permanently.</p>
              </div>
  
              <form class="flex items-start md:col-span-2">
                <button type="submit" class="rounded-md bg-red-600 px-3 py-2 text-sm font-semibold text-white shadow-sm hover:bg-red-500">Yes, delete my account</button>
              </form>
            </div>
          </div>
        </main>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  import { Dialog, DialogPanel, TransitionChild, TransitionRoot } from '@headlessui/vue'
  import {
    ChartBarSquareIcon,
    Cog6ToothIcon,
    FolderIcon,
    GlobeAltIcon,
    ServerIcon,
    SignalIcon,
    XMarkIcon,
  } from '@heroicons/vue/24/outline'
  import { Bars3Icon, MagnifyingGlassIcon } from '@heroicons/vue/20/solid'
  import { ChevronDownIcon } from '@heroicons/vue/16/solid'
  
  const navigation = [
    { name: 'Projects', href: '#', icon: FolderIcon, current: false },
    { name: 'Deployments', href: '#', icon: ServerIcon, current: false },
    { name: 'Activity', href: '#', icon: SignalIcon, current: false },
    { name: 'Domains', href: '#', icon: GlobeAltIcon, current: false },
    { name: 'Usage', href: '#', icon: ChartBarSquareIcon, current: false },
    { name: 'Settings', href: '#', icon: Cog6ToothIcon, current: true },
  ]
  const teams = [
    { id: 1, name: 'Planetaria', href: '#', initial: 'P', current: false },
    { id: 2, name: 'Protocol', href: '#', initial: 'P', current: false },
    { id: 3, name: 'Tailwind Labs', href: '#', initial: 'T', current: false },
  ]
  const secondaryNavigation = [
    { name: 'Account', href: '#', current: true },
    // { name: 'Notifications', href: '#', current: false },
    { name: 'Billing', href: '/billing', current: false },
    // { name: 'Teams', href: '#', current: false },
    // { name: 'Integrations', href: '#', current: false },
  ]
  
  const sidebarOpen = ref(false)
  </script>