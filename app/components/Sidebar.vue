<template>
    <div class="w-96 flex-shrink-0 border-r border-gray-200">
        <div class="p-6 border-b border-gray-200">
            <div class="space-y-1">
                <h1 class="text-2xl font-bold">Pedágio Fácil</h1>
                <p class="text-sm">Planeje sua viagem pelo Brasil</p>
            </div>
        </div>

        <div class="border-b border-gray-200">
            <div class="flex">
                <button
                    v-for="(tab, index) in tabs"
                    :key="tab.label"
                    @click="activeTab = index"
                    :class="[
                        'flex flex-1 items-center justify-center gap-2 p-4 text-sm font-semibold transition-colors',
                        activeTab === index
                            ? 'bg-black text-white'
                            : 'text-muted-foreground hover:text-foreground hover:bg-gray-100',
                    ]"
                >
                    <Icon :name="tab.icon" class="h-4 w-4" />
                    <span>{{ tab.label }}</span>
                </button>
            </div>
        </div>

        <div>
            <component :is="tabs[activeTab]?.content" />
        </div>
    </div>
</template>

<script setup lang="ts">
import Data from "./Data.vue";
import Summary from "./Summary.vue";
import Tolls from "./Tolls.vue";

interface TabItem {
    label: string;
    icon: string;
    content: any;
}

const tabs: TabItem[] = [
    {
        label: "Dados",
        icon: "mdi:document",
        content: Data,
    },
    {
        label: "Resumo",
        icon: "mdi:transit-connection-variant",
        content: Summary,
    },
    {
        label: "Pedágios",
        icon: "mdi:map",
        content: Tolls,
    },
];

const activeTab = useState<number>("activeTab", () => 0);
</script>
