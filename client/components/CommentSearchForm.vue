<template>
    <div class="relative">
        <span class="absolute inset-y-0 left-0 flex items-center pl-2">
            <button
                type="submit"
                class="p-1 focus:outline-none focus:shadow-outline"
            >
                <svg
                    fill="none"
                    stroke="currentColor"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    viewBox="0 0 24 24"
                    class="w-6 h-6"
                >
                    <path
                        d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"
                    ></path>
                </svg>
            </button>
        </span>
        <input
            type="search"
            name="query"
            class="py-2 text-sm border rounded-full pl-10 pr-2 focus:outline-none w-full max-w-[512px]"
            placeholder="Search..."
            autocomplete="off"
            v-model="state.query"
            @input="handleSearch"
        />
    </div>
    <p v-if="state.query" class="text-gray-500">Searching: {{ state.query }}</p>
</template>

<script setup lang="ts">
const state = reactive({
    query: "",
});

const emits = defineEmits(["handleSearch"]);

function handleSearch(e: Event) {
    e.preventDefault();

    emits("handleSearch", state.query);
}
</script>
