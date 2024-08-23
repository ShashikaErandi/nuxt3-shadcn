<template>
    <div class="grid gap-8">
        <header class="flex items-start justify-between">
            <div class="grow">
                <p>Hi, Welcome back!</p>
                <h1>Dashboard</h1>
            </div>
            <div class="bg-neutral-200 w-[120px] h-[36px]"></div>
        </header>
        <main class="grid gap-4">
            <Tabs default-value="Today" @click="setCategory">
                <TabsList class="max-w-[400px]">
                    <TabsTrigger v-for="item, index in list" :key="index" :value="item.title">
                        {{item.title}}
                    </TabsTrigger>
                </TabsList>
                <TabsContent v-for="item, index in list" :key="index" :value="item.title">
                    <Chart v-if="data.length > 0" :currentCategory="currentCategory" :data="data" />
                </TabsContent>
            </Tabs>
            <!-- <div class="flex items-center gap-4">
                <div v-for="(item, index) in 3" :key="index" class="w-[120px] h-[36px] bg-neutral-200"></div>
            </div>
            <section>
                <div class="w-full h-[360px] bg-neutral-200" ></div>
            </section> -->
        </main>
        <footer>
            <div class="grid lg:grid-cols-3">
                <Card v-for="(item, index) in cards" :key="index" :card="item"></Card>
            </div>
        </footer>
    </div>
</template>

<script setup lang='ts'>

import { Tabs, TabsContent, TabsList, TabsTrigger } from '@/components/ui/tabs'

let data = ref([])
const list = [
    {
        title: "Today",
        component: resolveComponent("TabsToday")
    },
    {
        title: "Week",
        component: "Week"
    },
    {
        title: "Year",
        component: "Year"
    }
]

let currentCategory = ref('today')

const setCategory = (e) => {
    let v = e.target.innerText.toLowerCase()
    currentCategory.value = v
    switch (v) {
        case 'today':
            generateRandomData(24)
        case 'week':
            generateRandomData(7)
        case 'year':
            generateRandomData(24)
        default:
    }

}

function generateRandomData(number = 7) {
    let values = []
    for (let i = 0; i < number + 1; i++) {
        values.push(Math.floor(Math.random() * 100))
    }
    data.value = values
    return values
}

const cards = [
    {
        title: "Sales",
        progression: 12,
        amount: 1244.23,
        lable: "View sales",
        description: "Sales of March 2024",
        icon: "solar:ticket-sale-outline"
    },
    {
        title: "Refund",
        progression: 8,
        amount: 84.44,
        lable: "View refund",
        description: "Refund since begining of year",
        icon: "heroicons-outline:receipt-refund"
    },
    {
        title: "Payouts",
        progression: 14,
        amount: 899.99,
        lable: "View payouts",
        description: "Payouts of this week",
        icon: "tabler:zoom-money"
    }
]

onMounted(() => {
    generateRandomData(24)
})
</script>

<style scoped></style>