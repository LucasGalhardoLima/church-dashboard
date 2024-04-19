<template>
    <NuxtLayout name="content">
        <template #title>
            <h1>Início</h1>
        </template>
        <template #actions>
            <div class="flex items-stretch flex-shrink-0 gap-1.5">
                <div class="relative inline-flex">
                    <UButton class="disabled:cursor-not-allowed disabled:opacity-75 inline-flex items-center"
                        icon="i-heroicons-bell" size="md" variant="ghost" :ui="{ rounded: 'rounded-full' }">
                        <span
                            class="absolute rounded-full ring-1 ring-white dark:ring-gray-900 flex items-center justify-center text-white dark:text-gray-900 font-medium whitespace-nowrap h-2 min-w-[0.5rem] text-[7px] p-0.5 top-2 right-3 bg-red-500 dark:bg-red-400"></span>

                    </UButton>

                </div>
            </div>
        </template>
        Conteúdo da página inicial
    </NuxtLayout>
</template>