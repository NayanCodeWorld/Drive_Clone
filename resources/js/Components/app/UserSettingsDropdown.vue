<template>
    <Menu as="div" class="relative inline-block text-left">
        <div>
            <MenuButton
                class="inline-flex w-full justify-center bg-gray-200 rounded-md px-4 py-2 text-sm font-medium text-gray-800 hover:bg-black/30 focus:outline-none focus-visible:ring-2 focus-visible:ring-white/75"
            >
                {{ $page.props.auth.user.name }}
                <svg
                    class="ml-2 -mr-1 h-5 text-gray-800"
                    xmlns="http://www.w3.org/2000/svg"
                    fill="none"
                    viewBox="0 0 24 24"
                    stroke-width="1.5"
                    stroke="currentColor"
                >
                    <path
                        stroke-linecap="round"
                        stroke-linejoin="round"
                        d="m19.5 8.25-7.5 7.5-7.5-7.5"
                    />
                </svg>
            </MenuButton>
        </div>

        <transition
            enter-active-class="transition duration-100 ease-out"
            enter-from-class="transform scale-95 opacity-0"
            enter-to-class="transform scale-100 opacity-100"
            leave-active-class="transition duration-75 ease-in"
            leave-from-class="transform scale-100 opacity-100"
            leave-to-class="transform scale-95 opacity-0"
        >
            <MenuItems
                class="absolute right-0 mt-2 w-32 origin-top-right divide-y divide-gray-100 rounded-md bg-white shadow-lg ring-1 ring-black/5 focus:outline-none"
            >
            <div class="px-1 py-1">
                <MenuItem v-slot="{ active }">
                  <ResponsiveNavLink :href="route('profile.edit')" class="[active ? 'bg-gray-100' : 'text-gray-800', 'px-4 py-2 text-sm']">
                    Profile
                  </ResponsiveNavLink>
                </MenuItem>

                <MenuItem v-slot="{ active }">
                  <ResponsiveNavLink  method="post" as="button" :href="route('logout')" class="[active ? 'bg-gray-100' : 'text-gray-800', 'px-4 py-2 text-sm']">
                    Logout
                  </ResponsiveNavLink>
                </MenuItem>
            </div>
            </MenuItems>
        </transition>
    </Menu>
</template>

<script setup>
import { Menu, MenuButton, MenuItems, MenuItem } from "@headlessui/vue";
import ResponsiveNavLink from "../ResponsiveNavLink.vue";
</script>
