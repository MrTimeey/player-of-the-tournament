<script setup lang="ts">
import { RouterView } from 'vue-router';
import DefaultLayout from '@/layouts/DefaultLayout.vue';
import DefaultFooter from '@/components/DefaultFooter.vue';
import DefaultHeader from '@/components/DefaultHeader.vue';
</script>

<template>
    <div class="bg-red-600">
        <default-layout>
            <template #header>
                <default-header />
            </template>

            <template #main>
                <div class="bg-gray-900">
                    <RouterView />
                </div>
            </template>
            <template #footer> <default-footer /></template>
        </default-layout>
    </div>
</template>

<style scoped></style>
