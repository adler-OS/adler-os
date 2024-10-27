<template>
  <div>
    <div class="sm:hidden">
      <label for="tabs" class="sr-only">Select a tab</label>
      <!-- Use an "onChange" listener to redirect the user to the selected tab URL. -->
      <select
        id="tabs"
        name="tabs"
        class="block w-full rounded-md border-gray-300 focus:border-indigo-500 focus:ring-indigo-500"
      >
        <option v-for="tab in tabs" :key="tab.name" :selected="tab.current">{{ tab.name }}</option>
      </select>
    </div>
    <div class="hidden sm:block">
      <div class="border-b border-gray-200">
        <nav class="-mb-px flex space-x-8" aria-label="Tabs">
          <a
            v-for="tab in tabs"
            :key="tab.name"
            :href="tab.href"
            :class="[
              tab.current
                ? 'border-indigo-500 text-indigo-600'
                : 'border-transparent text-gray-500 hover:border-gray-300 hover:text-gray-700',
              'group inline-flex items-center border-b-2 px-1 py-4 text-sm font-medium',
            ]"
            :aria-current="tab.current ? 'page' : undefined"
          >
            <component
              :is="tab.icon"
              :class="[
                tab.current ? 'text-indigo-500' : 'text-gray-400 group-hover:text-gray-500',
                '-ml-0.5 mr-2 h-5 w-5',
              ]"
              aria-hidden="true"
            />
            <span>{{ tab.name }}</span>
          </a>
        </nav>
      </div>
    </div>
  </div>
</template>

<script setup>
import { BuildingOfficeIcon, CreditCardIcon, UserIcon, UsersIcon } from "@heroicons/vue/20/solid";

const tabs = [
  { name: "Authentication", href: "#", icon: UserIcon, current: false },
  // { name: "Company", href: "#", icon: BuildingOfficeIcon, current: false },
  // { name: "Team Members", href: "#", icon: UsersIcon, current: false },
  { name: "Payment", href: "#", icon: CreditCardIcon, current: false },
];
</script>
