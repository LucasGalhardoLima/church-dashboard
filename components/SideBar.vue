<script setup lang="ts">
const links = [{
    label: 'Início',
    icon: 'i-heroicons-home',
    to: '/'
}, {
    label: 'Escalas',
    icon: 'i-heroicons-musical-note',
    to: '/band'
},
{
    label: 'Usuários',
    icon: 'i-heroicons-users',
    to: '/users'
},
{
    label: 'Configurações',
    icon: 'i-heroicons-cog',
    to: '/settings'
},
{
    label: 'Financeiro',
    icon: 'i-heroicons-currency-dollar',
    to: '/financial'
},
]

const logoLink = 'https://scontent-gru2-1.xx.fbcdn.net/v/t39.30808-6/326348237_1886148091732314_691957993630922162_n.jpg?_nc_cat=111&ccb=1-7&_nc_sid=5f2048&_nc_ohc=b3n_Vgf_Eg0Ab4XAkvE&_nc_ht=scontent-gru2-1.xx&oh=00_AfD3VJgM_ZHjjieFFfzWbAveSRvgQVziaM7_Kd2UfVlBxw&oe=66278B8E'
</script>

<template>
    <div
        class="flex-col items-stretch relative w-full border-b lg:border-b-0 lg:border-r border-gray-200 dark:border-gray-800 flex-shrink-0 hidden lg:flex lg:w-[250px]">
        <header
            class="h-[4rem] flex-shrink-0 flex items-center border-b border-gray-200 dark:border-gray-800 px-4 py-2 gap-x-4 min-w-0 !border-transparent">
            <UAvatar :src="logoLink" alt="Avatar" />
            <h1 class="text-lg font-semibold text-gray-800 dark:text-gray-200">Koinonia</h1>
        </header>
        <div class="flex flex-col w-full flex-1 relative overflow-hidden">
            <div class="flex-grow flex flex-col min-h-0 gap-y-2 py-2">
                <div class="flex-1 px-4 flex flex-col gap-y-2 overflow-y-auto">
                    <ul class="relative !min-h-[auto] !min-w-[auto]">
                        <li class="!overflow-visible" v-for="link in links" :key="link.label">
                            <div default-open="true" as="div">
                                <div as="template">
                                    <ULink :to="link.to"
                                        class="group relative flex items-center gap-1.5 px-2.5 py-1.5 w-full rounded-md font-medium text-sm focus:outline-none focus-visible:outline-none dark:focus-visible:outline-none focus-visible:before:ring-inset focus-visible:before:ring-2 focus-visible:before:ring-primary-500 dark:focus-visible:before:ring-primary-400 before:absolute before:inset-px before:rounded-md disabled:cursor-not-allowed disabled:opacity-75 hover:text-gray-900 dark:hover:text-white hover:before:bg-gray-200/50 dark:hover:before:bg-gray-800/50"
                                        active-class="text-gray-900 dark:text-gray hover:text-gray-800 dark:hover:text-white before:bg-gray-200/50 dark:before:bg-gray-800/50"
                                        inactive-class="text-gray-500 dark:text-gray-400 hover:text-gray-900 dark:hover:text-white">
                                        <UIcon :name="link.icon" class="w-5 h-5" />
                                        <span class="text-sm truncate relative">{{ link.label }}</span>
                                    </ULink>
                                </div>
                            </div>

                        </li>
                    </ul>
                </div>
            </div>
        </div>
    </div>
</template>