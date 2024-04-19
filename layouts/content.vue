<script setup lang="ts">
import { ref } from 'vue'
import { Dialog, DialogPanel, TransitionChild, TransitionRoot } from '@headlessui/vue'

const route = useRoute()

const sidebarOpen = ref(false)

const links = ref([{
    label: 'Início',
    icon: 'i-heroicons-home',
    to: '/',
    current: true,
}, {
    label: 'Escalas',
    icon: 'i-heroicons-musical-note',
    to: '/band',
    current: false,
},
{
    label: 'Membros',
    icon: 'i-heroicons-users',
    to: '/members',
    current: false,
},
{
    label: 'Configurações',
    icon: 'i-heroicons-cog',
    to: '/settings',
    current: false,
},
{
    label: 'Financeiro',
    icon: 'i-heroicons-currency-dollar',
    to: '/financial',
    current: false,
},
])


const changeRoute = (to: string) => {
    links.value.forEach(link => {
        link.current = link.to === to
    })
}

onMounted(() => {
    changeRoute(route.path)
})

</script>

<template>
    <div class="flex-col items-stretch relative w-full flex-1 flex">
        <TransitionRoot as="template" :show="sidebarOpen">
            <Dialog as="div" class="relative z-50 lg:hidden" @close="sidebarOpen = false">
                <TransitionChild as="template" enter="transition-opacity ease-linear duration-300"
                    enter-from="opacity-0" enter-to="opacity-100" leave="transition-opacity ease-linear duration-300"
                    leave-from="opacity-100" leave-to="opacity-0">
                    <div class="fixed inset-0 bg-gray-900/80" />
                </TransitionChild>

                <div class="fixed inset-0 flex">
                    <TransitionChild as="template" enter="transition ease-in-out duration-300 transform"
                        enter-from="-translate-x-full" enter-to="translate-x-0"
                        leave="transition ease-in-out duration-300 transform" leave-from="translate-x-0"
                        leave-to="-translate-x-full">
                        <DialogPanel class="relative mr-16 flex w-full max-w-xs flex-1">
                            <TransitionChild as="template" enter="ease-in-out duration-300" enter-from="opacity-0"
                                enter-to="opacity-100" leave="ease-in-out duration-300" leave-from="opacity-100"
                                leave-to="opacity-0">
                                <div class="absolute left-full top-0 flex w-16 justify-center pt-5">
                                    <button type="button" class="-m-2.5 p-2.5" @click="sidebarOpen = false">
                                        <span class="sr-only">Close sidebar</span>
                                        <UIcon name="i-heroicons-x-20-solid" class="h-6 w-6 text-white" aria-hidden="true" />
                                    </button>
                                </div>
                            </TransitionChild>
                            <!-- Sidebar component, swap this element with another sidebar if you like -->
                            <div class="flex grow flex-col gap-y-5 overflow-y-auto bg-primary px-6 pb-2">
                                <div class="flex h-16 shrink-0 items-center">
                                    <img class="h-8 w-auto" src="https://tailwindui.com/img/logos/mark.svg?color=white"
                                        alt="Your Company" />
                                </div>
                                <nav class="flex flex-1 flex-col">
                                    <ul role="list" class="flex flex-1 flex-col gap-y-7">
                                        <li>
                                            <ul role="list" class="-mx-2 space-y-1">
                                                <li v-for="link in links" :key="link.label">
                                                    <ULink :to="link.to" aria-hidden="true"
                                                        :class="[link.current ? 'bg-primary-700 text-white' : 'text-primary-200 hover:text-white hover:bg-primary-700', 'group flex gap-x-3 rounded-md p-2 text-sm leading-6 font-semibold']"
                                                        @click="changeRoute(link.to)">
                                                        <UIcon :name="link.icon" class="w-5 h-5" />
                                                        <span class="text-sm truncate relative">{{ link.label }}</span>
                                                    </ULink>
                                                </li>
                                            </ul>
                                        </li>
                                    </ul>
                                </nav>
                            </div>
                        </DialogPanel>
                    </TransitionChild>
                </div>
            </Dialog>
        </TransitionRoot>

        <div>
            <header
                class="h-[4rem] flex-shrink-0 flex items-center border-b border-gray-200 dark:border-gray-800 px-4 gap-x-4 min-w-0">
                <div class="flex items-center justify-between flex-1 gap-x-1.5 min-w-0">
                    <div class="flex items-stretch gap-1.5 min-w-0">
                        <UButton class="lg:hidden disabled:cursor-not-allowed disabled:opacity-75"
                            icon="i-heroicons-bars-3-20-solid" size="sm" color="primary" square variant="solid" @click="sidebarOpen = true" />
                        <h1 class="flex items-center gap-1.5 font-semibold text-gray-900 dark:text-white min-w-0">
                            <span class="truncate">
                                <slot name="title" />
                            </span>
                        </h1>
                    </div>
                    <slot name="actions" />
                </div>
            </header>
            <main class="py-4 px-4">
                <slot />
            </main>
        </div>
    </div>
</template>