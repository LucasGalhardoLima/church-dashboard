<template>
    <div class="flex-col items-stretch relative w-full flex-1 flex">
        <header
            class="h-[4rem] flex-shrink-0 flex items-center border-b border-gray-200 dark:border-gray-800 px-4 gap-x-4 min-w-0">
            <div class="flex items-center justify-between flex-1 gap-x-1.5 min-w-0">
                <div class="flex items-stretch gap-1.5 min-w-0">
                    <UButton class="lg:hidden disabled:cursor-not-allowed disabled:opacity-75"
                        icon="i-heroicons-bars-3-20-solid" size="sm" color="primary" square variant="solid" />
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
</template>