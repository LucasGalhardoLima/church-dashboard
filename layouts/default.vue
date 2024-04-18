<script setup lang="ts">
import { SpeedInsights } from "@vercel/speed-insights/vue";
</script>


<template>
    <div class="fixed inset-0 flex overflow-hidden">
        <SpeedInsights />
        <SideBar />
        <MainContainer>
            <slot />
        </MainContainer>

    </div>
</template>