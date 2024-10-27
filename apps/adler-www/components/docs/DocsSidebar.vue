<template>
  <nav class="flex flex-1 flex-col" aria-label="Sidebar">
    <ul role="list" class="flex flex-1 flex-col gap-y-7">
      <li>
        <ul role="list" class="-mx-2 space-y-1">
          <li v-for="item in navigation" :key="item.name">
            <a
              :href="item.href"
              :class="[
                item.current ? 'bg-gray-100 text-indigo-600' : 'text-gray-700 hover:bg-gray-100 hover:text-indigo-600',
                'group flex gap-x-3 rounded-md p-2 text-sm font-semibold leading-6',
              ]"
            >
              <component
                :is="item.icon"
                :class="[
                  item.current ? 'text-indigo-600' : 'text-gray-400 group-hover:text-indigo-600',
                  'h-6 w-6 shrink-0',
                ]"
                aria-hidden="true"
              />
              {{ item.name }}
              <span
                v-if="item.count"
                class="ml-auto w-9 min-w-max whitespace-nowrap rounded-full bg-gray-50 px-2.5 py-0.5 text-center text-xs font-medium leading-5 text-gray-600 ring-1 ring-inset ring-gray-200"
                aria-hidden="true"
                >{{ item.count }}</span
              >
            </a>
          </li>
        </ul>
      </li>
      <li v-if="false">
        <div class="text-xs font-semibold leading-6 text-gray-400">Projects</div>
        <ul role="list" class="-mx-2 mt-2 space-y-1">
          <li v-for="item in secondaryNavigation" :key="item.name">
            <a
              :href="item.href"
              :class="[
                item.current ? 'bg-gray-50 text-indigo-600' : 'text-gray-700 hover:bg-gray-100 hover:text-indigo-600',
                'group flex gap-x-3 rounded-md p-2 text-sm font-semibold leading-6',
              ]"
            >
              <span
                :class="[
                  item.current
                    ? 'border-indigo-600 text-indigo-600'
                    : 'border-gray-200 text-gray-400 group-hover:border-indigo-600 group-hover:text-indigo-600',
                  'flex h-6 w-6 shrink-0 items-center justify-center rounded-lg border bg-white text-[0.625rem] font-medium',
                ]"
                >{{ item.initial }}</span
              >
              <span class="truncate">{{ item.name }}</span>
            </a>
          </li>
        </ul>
      </li>
    </ul>
  </nav>
</template>

<script setup>
import {
  CalendarIcon,
  ChartPieIcon,
  DocumentDuplicateIcon,
  FolderIcon,
  HomeIcon,
  CreditCardIcon,
  UserIcon,
} from "@heroicons/vue/24/outline";

const navigation = [
  { name: "Authentication", href: "#", icon: UserIcon, count: "5", current: true },
  { name: "Payment", href: "#", icon: CreditCardIcon, current: false },
  // { name: "Projects", href: "#", icon: FolderIcon, count: "12", current: false },
  // { name: "Calendar", href: "#", icon: CalendarIcon, count: "20+", current: false },
  // { name: "Documents", href: "#", icon: DocumentDuplicateIcon, current: false },
  // { name: "Reports", href: "#", icon: ChartPieIcon, current: false },
];
const secondaryNavigation = [
  { name: "Website redesign", href: "#", initial: "W", current: false },
  { name: "GraphQL API", href: "#", initial: "G", current: false },
  { name: "Customer migration guides", href: "#", initial: "C", current: false },
  { name: "Profit sharing program", href: "#", initial: "P", current: false },
];
</script>
