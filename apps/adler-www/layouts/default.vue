<template>
  <div class="min-h-screen bg-gray-200">
    <header>
      <Disclosure as="nav" class="bg-gray-800" v-slot="{ open }">
        <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
          <div class="flex h-16 justify-between items-center">
            <div class="flex">
              <div class="-ml-2 mr-2 flex items-center md:hidden">
                <!-- Mobile menu button -->
                <DisclosureButton
                  class="relative inline-flex items-center justify-center rounded-md p-2 text-gray-400 hover:bg-gray-700 hover:text-white focus:outline-none focus:ring-2 focus:ring-inset focus:ring-white"
                >
                  <span class="absolute -inset-0.5" />
                  <span class="sr-only">Open main menu</span>
                  <Bars3Icon v-if="!open" class="block h-6 w-6" aria-hidden="true" />
                  <XMarkIcon v-else class="block h-6 w-6" aria-hidden="true" />
                </DisclosureButton>
              </div>
              <div class="flex flex-shrink-0 items-center text-white font-bold text-lg">
                <!-- <img
                  class="h-8 w-auto"
                  src="https://tailwindui.com/plus/img/logos/mark.svg?color=indigo&shade=500"
                  alt="Your Company"
                /> -->
                🇩🇪 Adler OS
              </div>
              <div class="hidden md:ml-6 md:flex md:items-center md:space-x-4">
                <a
                  v-for="item in navigation"
                  :key="item.name"
                  :href="item.href"
                  :class="[
                    isCurrentRoute(item.href)
                      ? 'bg-gray-900 text-white'
                      : 'text-gray-300 hover:bg-gray-700 hover:text-white',
                    'rounded-md px-3 py-2 text-sm font-medium',
                  ]"
                  :aria-current="isCurrentRoute(item.href) ? 'page' : undefined"
                  >{{ item.name }}</a
                >
              </div>
            </div>
            <div class="flex items-center">
              <github-button
                href="https://github.com/adler-os/adler-os"
                data-color-scheme="no-preference: light; light: light; dark: dark;"
                data-size="large"
                data-show-count="true"
                aria-label="Star adler-os/adler-os on GitHub"
                >Star</github-button
              >
              <div v-if="hidden" class="flex-shrink-0">
                <button
                  type="button"
                  class="relative inline-flex items-center gap-x-1.5 rounded-md bg-indigo-500 px-3 py-2 text-sm font-semibold text-white shadow-sm hover:bg-indigo-400 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-500"
                >
                  <PlusIcon class="-ml-0.5 h-5 w-5" aria-hidden="true" />
                  New Job
                </button>
              </div>
              <div v-if="hidden" class="hidden md:ml-4 md:flex md:flex-shrink-0 md:items-center">
                <button
                  type="button"
                  class="relative rounded-full bg-gray-800 p-1 text-gray-400 hover:text-white focus:outline-none focus:ring-2 focus:ring-white focus:ring-offset-2 focus:ring-offset-gray-800"
                >
                  <span class="absolute -inset-1.5" />
                  <span class="sr-only">View notifications</span>
                  <BellIcon class="h-6 w-6" aria-hidden="true" />
                </button>
                <!-- Profile dropdown -->
                <Menu as="div" class="relative ml-3">
                  <div>
                    <MenuButton
                      class="relative flex rounded-full bg-gray-800 text-sm focus:outline-none focus:ring-2 focus:ring-white focus:ring-offset-2 focus:ring-offset-gray-800"
                    >
                      <span class="absolute -inset-1.5" />
                      <span class="sr-only">Open user menu</span>
                      <img class="h-8 w-8 rounded-full" :src="user.imageUrl" alt="" />
                    </MenuButton>
                  </div>
                  <transition
                    enter-active-class="transition ease-out duration-200"
                    enter-from-class="transform opacity-0 scale-95"
                    enter-to-class="transform opacity-100 scale-100"
                    leave-active-class="transition ease-in duration-75"
                    leave-from-class="transform opacity-100 scale-100"
                    leave-to-class="transform opacity-0 scale-95"
                  >
                    <MenuItems
                      class="absolute right-0 z-10 mt-2 w-48 origin-top-right rounded-md bg-white py-1 shadow-lg ring-1 ring-black ring-opacity-5 focus:outline-none"
                    >
                      <MenuItem v-for="item in userNavigation" :key="item.name" v-slot="{ active }">
                        <nuxt-link
                          :to="item.href"
                          :class="[active ? 'bg-gray-100' : '', 'block px-4 py-2 text-sm text-gray-700']"
                          >{{ item.name }}</nuxt-link
                        >
                      </MenuItem>
                    </MenuItems>
                  </transition>
                </Menu>
              </div>
            </div>
          </div>
        </div>
        <DisclosurePanel class="md:hidden">
          <div class="space-y-1 px-2 pb-3 pt-2 sm:px-3">
            <DisclosureButton
              v-for="item in navigation"
              :key="item.name"
              as="a"
              :href="item.href"
              :class="[
                item.current ? 'bg-gray-900 text-white' : 'text-gray-300 hover:bg-gray-700 hover:text-white',
                'block rounded-md px-3 py-2 text-base font-medium',
              ]"
              :aria-current="item.current ? 'page' : undefined"
              >{{ item.name }}</DisclosureButton
            >
          </div>
          <div class="border-t border-gray-700 pb-3 pt-4">
            <div class="flex items-center px-5 sm:px-6">
              <div class="flex-shrink-0">
                <img class="h-10 w-10 rounded-full" :src="user.imageUrl" alt="" />
              </div>
              <div class="ml-3">
                <div class="text-base font-medium text-white">{{ user.name }}</div>
                <div class="text-sm font-medium text-gray-400">{{ user.email }}</div>
              </div>
              <button
                type="button"
                class="relative ml-auto flex-shrink-0 rounded-full bg-gray-800 p-1 text-gray-400 hover:text-white focus:outline-none focus:ring-2 focus:ring-white focus:ring-offset-2 focus:ring-offset-gray-800"
              >
                <span class="absolute -inset-1.5" />
                <span class="sr-only">View notifications</span>
                <BellIcon class="h-6 w-6" aria-hidden="true" />
              </button>
            </div>
            <div class="mt-3 space-y-1 px-2 sm:px-3">
              <DisclosureButton
                v-for="item in userNavigation"
                :key="item.name"
                as="a"
                :href="item.href"
                class="block rounded-md px-3 py-2 text-base font-medium text-gray-400 hover:bg-gray-700 hover:text-white"
                >{{ item.name }}</DisclosureButton
              >
            </div>
          </div>
        </DisclosurePanel>
      </Disclosure>
    </header>
    <main class="py-20">
      <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
        <slot />
      </div>
    </main>
  </div>
</template>

<script setup>
import GithubButton from "vue-github-button";

import { Disclosure, DisclosureButton, DisclosurePanel, Menu, MenuButton, MenuItem, MenuItems } from "@headlessui/vue";
import { Bars3Icon, BellIcon, XMarkIcon } from "@heroicons/vue/24/outline";
import { PlusIcon } from "@heroicons/vue/20/solid";

const route = useRoute();

const user = {
  name: "Tom Cook",
  email: "tom@example.com",
  imageUrl:
    "https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80",
};

function isCurrentRoute(path) {
  return path === route.path;
}

const navigation = [
  { name: "Startseite", href: "/", current: true },
  // { name: "Dokumentation", href: "/docs", current: false },
  // { name: "Projects", href: "#", current: false },
  // { name: "Calendar", href: "#", current: false },
];
const userNavigation = [
  { name: "Your Profile", href: "#" },
  { name: "Settings", href: "#" },
  { name: "Sign out", href: "#" },
];
</script>
