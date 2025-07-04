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
                    v-for="tab in tabs"
                    :key="tab.label"
                    class="flex flex-1 items-center justify-center gap-2 p-4 text-sm font-semibold"
                >
                    <Icon :name="tab.icon" class="h-4 w-4" />
                    <span>{{ tab.label }}</span>
                </button>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
interface TabItem {
    label: string;
    icon: string;
    content: string;
}

const tabs = useState<TabItem[]>("tabs", () => [
    {
        label: "Dados",
        icon: "mdi:document",
        content: "Página de Dados",
    },
    {
        label: "Resumo",
        icon: "mdi:transit-connection-variant",
        content: "Página de Resumo",
    },
    {
        label: "Pedágios",
        icon: "mdi:map",
        content: "Página de Pedágios",
    },
]);
</script>
