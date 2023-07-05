<template>
    <Head title="Items" />

    <AuthenticatedLayout>
        <template #header>
            <div class="flex justify-between">
                <h2>Items</h2>
                <div>
                    <Link v-if="prop.auth.user.permissions.includes('create-item')" href="/items/create" class="px-4 py-2 bg-gray-100 border border-gray-300 rounded shadow hover:bg-white">
                        Create Item
                    </Link>
                </div>
            </div>
        </template>

        <div class="py-8">
            <div class="mx-auto max-w-7xl sm:px-6 lg:px-8">
                <div class="grid grid-flow-row grid-cols-3 gap-4 overflow-hidden shadow-sm sm:rounded-lg">
                    <ItemComponent v-for="item in items" :key="item.id" :item="item" />
                </div>
            </div>
        </div>

    </AuthenticatedLayout>
</template>

<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import ItemComponent from '@/Components/ItemComponent.vue';
import { Head, Link } from '@inertiajs/vue3';



const prop = defineProps({
    items: Array,
    auth: Object
})

</script>
