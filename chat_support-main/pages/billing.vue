<template>
<main class="lg:pl-72">
      <header class="relative isolate ">
        <div class="absolute inset-0 -z-10 overflow-hidden" aria-hidden="true">
          <div class="absolute top-full left-16 -mt-16 transform-gpu opacity-50 blur-3xl xl:left-1/2 xl:-ml-80">
            <div class="aspect-1154/678 w-[72.125rem] bg-linear-to-br from-[#FF80B5] to-[#9089FC]" style="clip-path: polygon(100% 38.5%, 82.6% 100%, 60.2% 37.7%, 52.4% 32.1%, 47.5% 41.8%, 45.2% 65.6%, 27.5% 23.4%, 0.1% 35.3%, 17.9% 0%, 27.7% 23.4%, 76.2% 2.5%, 74.2% 56%, 100% 38.5%)" />
          </div>
          <div class="absolute inset-x-0 bottom-0 h-px bg-gray-900/5" />
        </div>
  
        <div class="mx-auto max-w-7xl px-4 py-10 sm:px-6 lg:px-8">
          <div class="mx-auto flex max-w-2xl items-center justify-between gap-x-8 lg:mx-0 lg:max-w-none">
            <div class="flex items-center gap-x-6">
              <img src="https://tailwindcss.com/plus-assets/img/logos/48x48/tuple.svg" alt="" class="size-16 flex-none rounded-full ring-1 ring-gray-900/10" />
              <h1>
                <div class="text-sm/6 text-gray-500">Invoice <span class="text-gray-700">#00011</span></div>
                <div class="mt-1 text-base font-semibold text-gray-900">Tuple, Inc</div>
              </h1>
            </div>
            <div class="flex items-center gap-x-4 sm:gap-x-6">
              <button type="button" class="hidden text-sm/6 font-semibold text-gray-900 sm:block">Copy URL</button>
              <a href="#" class="hidden text-sm/6 font-semibold text-gray-900 sm:block">Edit</a>
              <a href="#" class="rounded-md bg-indigo-600 px-3 py-2 text-sm font-semibold text-white shadow-xs hover:bg-indigo-500 focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600">Send</a>
  
              <Menu as="div" class="relative sm:hidden">
                <MenuButton class="-m-3 block p-3">
                  <span class="sr-only">More</span>
                  <EllipsisVerticalIcon class="size-5 text-gray-500" aria-hidden="true" />
                </MenuButton>
  
                <transition enter-active-class="transition ease-out duration-100" enter-from-class="transform opacity-0 scale-95" enter-to-class="transform opacity-100 scale-100" leave-active-class="transition ease-in duration-75" leave-from-class="transform opacity-100 scale-100" leave-to-class="transform opacity-0 scale-95">
                  <MenuItems class="absolute right-0 z-10 mt-0.5 w-32 origin-top-right rounded-md bg-white py-2 shadow-lg ring-1 ring-gray-900/5 focus:outline-hidden">
                    <MenuItem v-slot="{ active }">
                      <button type="button" :class="[active ? 'bg-gray-50 outline-hidden' : '', 'block w-full px-3 py-1 text-left text-sm/6 text-gray-900']">Copy URL</button>
                    </MenuItem>
                    <MenuItem v-slot="{ active }">
                      <a href="#" :class="[active ? 'bg-gray-50 outline-hidden' : '', 'block px-3 py-1 text-sm/6 text-gray-900']">Edit</a>
                    </MenuItem>
                  </MenuItems>
                </transition>
              </Menu>
            </div>
          </div>
        </div>
      </header>
  
      <div class="mx-auto max-w-7xl px-4 py-16 sm:px-6 lg:px-8">
        <div class="mx-auto grid max-w-2xl grid-cols-1 grid-rows-1 items-start gap-x-8 gap-y-8 lg:mx-0 lg:max-w-none lg:grid-cols-3">
          <!-- Invoice summary -->
          <div class="lg:col-start-3 lg:row-end-1">
            <h2 class="sr-only">Summary</h2>
            <div class="rounded-lg bg-gray-50 shadow-xs ring-1 ring-gray-900/5">
              <dl class="flex flex-wrap">
                <div class="flex-auto pt-6 pl-6">
                  <dt class="text-sm/6 font-semibold text-gray-900">Amount</dt>
                  <dd class="mt-1 text-base font-semibold text-gray-900">$10,560.00</dd>
                </div>
                <div class="flex-none self-end px-6 pt-4">
                  <dt class="sr-only">Status</dt>
                  <dd class="rounded-md bg-green-50 px-2 py-1 text-xs font-medium text-green-600 ring-1 ring-green-600/20 ring-inset">Paid</dd>
                </div>
                <div class="mt-6 flex w-full flex-none gap-x-4 border-t border-gray-900/5 px-6 pt-6">
                  <dt class="flex-none">
                    <span class="sr-only">Client</span>
                    <UserCircleIcon class="h-6 w-5 text-gray-400" aria-hidden="true" />
                  </dt>
                  <dd class="text-sm/6 font-medium text-gray-900">Alex Curren</dd>
                </div>
                <div class="mt-4 flex w-full flex-none gap-x-4 px-6">
                  <dt class="flex-none">
                    <span class="sr-only">Due date</span>
                    <CalendarDaysIcon class="h-6 w-5 text-gray-400" aria-hidden="true" />
                  </dt>
                  <dd class="text-sm/6 text-gray-500">
                    <time datetime="2023-01-31">January 31, 2023</time>
                  </dd>
                </div>
                <div class="mt-4 flex w-full flex-none gap-x-4 px-6">
                  <dt class="flex-none">
                    <span class="sr-only">Status</span>
                    <CreditCardIcon class="h-6 w-5 text-gray-400" aria-hidden="true" />
                  </dt>
                  <dd class="text-sm/6 text-gray-500">Paid with MasterCard</dd>
                </div>
              </dl>
              <div class="mt-6 border-t border-gray-900/5 px-6 py-6">
                <a href="#" class="text-sm/6 font-semibold text-gray-900">Download receipt <span aria-hidden="true">&rarr;</span></a>
              </div>
            </div>
          </div>
  
          <!-- Invoice -->
          <div class="-mx-4 px-4 py-8 shadow-xs ring-1 ring-gray-900/5 sm:mx-0 sm:rounded-lg sm:px-8 sm:pb-14 lg:col-span-2 lg:row-span-2 lg:row-end-2 xl:px-16 xl:pt-16 xl:pb-20">
            <h2 class="text-base font-semibold text-gray-900">Invoice</h2>
            <dl class="mt-6 grid grid-cols-1 text-sm/6 sm:grid-cols-2">
              <div class="sm:pr-4">
                <dt class="inline text-gray-500">Issued on</dt>
                {{ ' ' }}
                <dd class="inline text-gray-700"><time datetime="2023-23-01">January 23, 2023</time></dd>
              </div>
              <div class="mt-2 sm:mt-0 sm:pl-4">
                <dt class="inline text-gray-500">Due on</dt>
                {{ ' ' }}
                <dd class="inline text-gray-700"><time datetime="2023-31-01">January 31, 2023</time></dd>
              </div>
              <div class="mt-6 border-t border-gray-900/5 pt-6 sm:pr-4">
                <dt class="font-semibold text-gray-900">From</dt>
                <dd class="mt-2 text-gray-500"><span class="font-medium text-gray-900">Acme, Inc.</span><br />7363 Cynthia Pass<br />Toronto, ON N3Y 4H8</dd>
              </div>
              <div class="mt-8 sm:mt-6 sm:border-t sm:border-gray-900/5 sm:pt-6 sm:pl-4">
                <dt class="font-semibold text-gray-900">To</dt>
                <dd class="mt-2 text-gray-500"><span class="font-medium text-gray-900">Tuple, Inc</span><br />886 Walter Street<br />New York, NY 12345</dd>
              </div>
            </dl>
            <table class="mt-16 w-full text-left text-sm/6 whitespace-nowrap">
              <colgroup>
                <col class="w-full" />
                <col />
                <col />
                <col />
              </colgroup>
              <thead class="border-b border-gray-200 text-gray-900">
                <tr>
                  <th scope="col" class="px-0 py-3 font-semibold">Projects</th>
                  <th scope="col" class="hidden py-3 pr-0 pl-8 text-right font-semibold sm:table-cell">Hours</th>
                  <th scope="col" class="hidden py-3 pr-0 pl-8 text-right font-semibold sm:table-cell">Rate</th>
                  <th scope="col" class="py-3 pr-0 pl-8 text-right font-semibold">Price</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="item in invoice.items" :key="item.id" class="border-b border-gray-100">
                  <td class="max-w-0 px-0 py-5 align-top">
                    <div class="truncate font-medium text-gray-900">{{ item.title }}</div>
                    <div class="truncate text-gray-500">{{ item.description }}</div>
                  </td>
                  <td class="hidden py-5 pr-0 pl-8 text-right align-top text-gray-700 tabular-nums sm:table-cell">{{ item.hours }}</td>
                  <td class="hidden py-5 pr-0 pl-8 text-right align-top text-gray-700 tabular-nums sm:table-cell">{{ item.rate }}</td>
                  <td class="py-5 pr-0 pl-8 text-right align-top text-gray-700 tabular-nums">{{ item.price }}</td>
                </tr>
              </tbody>
              <tfoot>
                <tr>
                  <th scope="row" class="px-0 pt-6 pb-0 font-normal text-gray-700 sm:hidden">Subtotal</th>
                  <th scope="row" colspan="3" class="hidden px-0 pt-6 pb-0 text-right font-normal text-gray-700 sm:table-cell">Subtotal</th>
                  <td class="pt-6 pr-0 pb-0 pl-8 text-right text-gray-900 tabular-nums">{{ invoice.subTotal }}</td>
                </tr>
                <tr>
                  <th scope="row" class="pt-4 font-normal text-gray-700 sm:hidden">Tax</th>
                  <th scope="row" colspan="3" class="hidden pt-4 text-right font-normal text-gray-700 sm:table-cell">Tax</th>
                  <td class="pt-4 pr-0 pb-0 pl-8 text-right text-gray-900 tabular-nums">{{ invoice.tax }}</td>
                </tr>
                <tr>
                  <th scope="row" class="pt-4 font-semibold text-gray-900 sm:hidden">Total</th>
                  <th scope="row" colspan="3" class="hidden pt-4 text-right font-semibold text-gray-900 sm:table-cell">Total</th>
                  <td class="pt-4 pr-0 pb-0 pl-8 text-right font-semibold text-gray-900 tabular-nums">{{ invoice.total }}</td>
                </tr>
              </tfoot>
            </table>
          </div>
  
          <div class="lg:col-start-3">
            <!-- Activity feed -->
            <h2 class="text-sm/6 font-semibold text-gray-900">Activity</h2>
            <ul role="list" class="mt-6 space-y-6">
              <li v-for="(activityItem, activityItemIdx) in activity" :key="activityItem.id" class="relative flex gap-x-4">
                <div :class="[activityItemIdx === activity.length - 1 ? 'h-6' : '-bottom-6', 'absolute top-0 left-0 flex w-6 justify-center']">
                  <div class="w-px bg-gray-200" />
                </div>
                <template v-if="activityItem.type === 'commented'">
                  <img :src="activityItem.person.imageUrl" alt="" class="relative mt-3 size-6 flex-none rounded-full bg-gray-50" />
                  <div class="flex-auto rounded-md p-3 ring-1 ring-gray-200 ring-inset">
                    <div class="flex justify-between gap-x-4">
                      <div class="py-0.5 text-xs/5 text-gray-500">
                        <span class="font-medium text-gray-900">{{ activityItem.person.name }}</span> commented
                      </div>
                      <time :datetime="activityItem.dateTime" class="flex-none py-0.5 text-xs/5 text-gray-500">{{ activityItem.date }}</time>
                    </div>
                    <p class="text-sm/6 text-gray-500">{{ activityItem.comment }}</p>
                  </div>
                </template>
                <template v-else>
                  <div class="relative flex size-6 flex-none items-center justify-center bg-white">
                    <CheckCircleIcon v-if="activityItem.type === 'paid'" class="size-6 text-indigo-600" aria-hidden="true" />
                    <div v-else class="size-1.5 rounded-full bg-gray-100 ring-1 ring-gray-300" />
                  </div>
                  <p class="flex-auto py-0.5 text-xs/5 text-gray-500">
                    <span class="font-medium text-gray-900">{{ activityItem.person.name }}</span> {{ activityItem.type }} the invoice.
                  </p>
                  <time :datetime="activityItem.dateTime" class="flex-none py-0.5 text-xs/5 text-gray-500">{{ activityItem.date }}</time>
                </template>
              </li>
            </ul>
  
            <!-- New comment form -->
            <div class="mt-6 flex gap-x-3">
              <img src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80" alt="" class="size-6 flex-none rounded-full bg-gray-50" />
              <form action="#" class="relative flex-auto">
                <div class="overflow-hidden rounded-lg pb-12 outline-1 -outline-offset-1 outline-gray-300 focus-within:outline-2 focus-within:-outline-offset-2 focus-within:outline-indigo-600">
                  <label for="comment" class="sr-only">Add your comment</label>
                  <textarea rows="2" name="comment" id="comment" class="block w-full resize-none bg-transparent px-3 py-1.5 text-base text-gray-900 placeholder:text-gray-400 focus:outline-none sm:text-sm/6" placeholder="Add your comment..." />
                </div>
  
                <div class="absolute inset-x-0 bottom-0 flex justify-between py-2 pr-2 pl-3">
                  <div class="flex items-center space-x-5">
                    <div class="flex items-center">
                      <button type="button" class="-m-2.5 flex size-10 items-center justify-center rounded-full text-gray-400 hover:text-gray-500">
                        <PaperClipIcon class="size-5" aria-hidden="true" />
                        <span class="sr-only">Attach a file</span>
                      </button>
                    </div>
                    <div class="flex items-center">
                      <Listbox as="div" v-model="selected">
                        <ListboxLabel class="sr-only">Your mood</ListboxLabel>
                        <div class="relative">
                          <ListboxButton class="relative -m-2.5 flex size-10 items-center justify-center rounded-full text-gray-400 hover:text-gray-500">
                            <span class="flex items-center justify-center">
                              <span v-if="selected.value === null">
                                <FaceSmileIcon class="size-5 shrink-0" aria-hidden="true" />
                                <span class="sr-only">Add your mood</span>
                              </span>
                              <span v-if="!(selected.value === null)">
                                <span :class="[selected.bgColor, 'flex size-8 items-center justify-center rounded-full']">
                                  <component :is="selected.icon" class="size-5 shrink-0 text-white" aria-hidden="true" />
                                </span>
                                <span class="sr-only">{{ selected.name }}</span>
                              </span>
                            </span>
                          </ListboxButton>
  
                          <transition leave-active-class="transition ease-in duration-100" leave-from-class="opacity-100" leave-to-class="opacity-0">
                            <ListboxOptions class="absolute bottom-10 z-10 -ml-6 w-60 rounded-lg bg-white py-3 text-base shadow-sm ring-1 ring-black/5 focus:outline-hidden sm:ml-auto sm:w-64 sm:text-sm">
                              <ListboxOption as="template" v-for="mood in moods" :key="mood.value" :value="mood" v-slot="{ active }">
                                <li :class="[active ? 'bg-gray-100' : 'bg-white', 'relative cursor-default px-3 py-2 select-none']">
                                  <div class="flex items-center">
                                    <div :class="[mood.bgColor, 'flex size-8 items-center justify-center rounded-full']">
                                      <component :is="mood.icon" :class="[mood.iconColor, 'size-5 shrink-0']" aria-hidden="true" />
                                    </div>
                                    <span class="ml-3 block truncate font-medium">{{ mood.name }}</span>
                                  </div>
                                </li>
                              </ListboxOption>
                            </ListboxOptions>
                          </transition>
                        </div>
                      </Listbox>
                    </div>
                  </div>
                  <button type="submit" class="rounded-md bg-white px-2.5 py-1.5 text-sm font-semibold text-gray-900 shadow-xs ring-1 ring-gray-300 ring-inset hover:bg-gray-50">Comment</button>
                </div>
              </form>
            </div>
          </div>
        </div>
      </div>
    </main>
  
    
  </template>
  
  <script setup>
  import { ref } from 'vue'
  import {
    Dialog,
    DialogPanel,
    Listbox,
    ListboxButton,
    ListboxLabel,
    ListboxOption,
    ListboxOptions,
    Menu,
    MenuButton,
    MenuItem,
    MenuItems,
  } from '@headlessui/vue'
  import {
    Bars3Icon,
    CalendarDaysIcon,
    CreditCardIcon,
    EllipsisVerticalIcon,
    FaceFrownIcon,
    FaceSmileIcon,
    FireIcon,
    HandThumbUpIcon,
    HeartIcon,
    PaperClipIcon,
    UserCircleIcon,
    XMarkIcon as XMarkIconMini,
  } from '@heroicons/vue/20/solid'
  import { BellIcon, XMarkIcon as XMarkIconOutline } from '@heroicons/vue/24/outline'
  import { CheckCircleIcon } from '@heroicons/vue/24/solid'
  
  const navigation = [
    { name: 'Home', href: '#' },
    { name: 'Invoices', href: '#' },
    { name: 'Clients', href: '#' },
    { name: 'Expenses', href: '#' },
  ]
  const invoice = {
    subTotal: '$8,800.00',
    tax: '$1,760.00',
    total: '$10,560.00',
    items: [
      {
        id: 1,
        title: 'Logo redesign',
        description: 'New logo and digital asset playbook.',
        hours: '20.0',
        rate: '$100.00',
        price: '$2,000.00',
      },
      {
        id: 2,
        title: 'Website redesign',
        description: 'Design and program new company website.',
        hours: '52.0',
        rate: '$100.00',
        price: '$5,200.00',
      },
      {
        id: 3,
        title: 'Business cards',
        description: 'Design and production of 3.5" x 2.0" business cards.',
        hours: '12.0',
        rate: '$100.00',
        price: '$1,200.00',
      },
      {
        id: 4,
        title: 'T-shirt design',
        description: 'Three t-shirt design concepts.',
        hours: '4.0',
        rate: '$100.00',
        price: '$400.00',
      },
    ],
  }
  const activity = [
    { id: 1, type: 'created', person: { name: 'Chelsea Hagon' }, date: '7d ago', dateTime: '2023-01-23T10:32' },
    { id: 2, type: 'edited', person: { name: 'Chelsea Hagon' }, date: '6d ago', dateTime: '2023-01-23T11:03' },
    { id: 3, type: 'sent', person: { name: 'Chelsea Hagon' }, date: '6d ago', dateTime: '2023-01-23T11:24' },
    {
      id: 4,
      type: 'commented',
      person: {
        name: 'Chelsea Hagon',
        imageUrl:
          'https://images.unsplash.com/photo-1550525811-e5869dd03032?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80',
      },
      comment: 'Called client, they reassured me the invoice would be paid by the 25th.',
      date: '3d ago',
      dateTime: '2023-01-23T15:56',
    },
    { id: 5, type: 'viewed', person: { name: 'Alex Curren' }, date: '2d ago', dateTime: '2023-01-24T09:12' },
    { id: 6, type: 'paid', person: { name: 'Alex Curren' }, date: '1d ago', dateTime: '2023-01-24T09:20' },
  ]
  const moods = [
    { name: 'Excited', value: 'excited', icon: FireIcon, iconColor: 'text-white', bgColor: 'bg-red-500' },
    { name: 'Loved', value: 'loved', icon: HeartIcon, iconColor: 'text-white', bgColor: 'bg-pink-400' },
    { name: 'Happy', value: 'happy', icon: FaceSmileIcon, iconColor: 'text-white', bgColor: 'bg-green-400' },
    { name: 'Sad', value: 'sad', icon: FaceFrownIcon, iconColor: 'text-white', bgColor: 'bg-yellow-400' },
    { name: 'Thumbsy', value: 'thumbsy', icon: HandThumbUpIcon, iconColor: 'text-white', bgColor: 'bg-blue-500' },
    { name: 'I feel nothing', value: null, icon: XMarkIconMini, iconColor: 'text-gray-400', bgColor: 'bg-transparent' },
  ]
  
  const mobileMenuOpen = ref(false)
  const selected = ref(moods[5])
  </script>