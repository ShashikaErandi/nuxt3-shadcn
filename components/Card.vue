<template>
    <Card>
        <CardHeader>
            <div class="flex items-center justify-between">
                <p>{{ card.title }}</p>
                <Badge class="bg-green-400">{{ '+' + card.progression + '%' }}</Badge>
            </div>
        </CardHeader>
        <CardContent class="flex item-center justify-end border-b pt-0 pb-2 px-4">
            <div class="text-[48px] font-[800]">
                <span class="text-neutral-300">$</span>
                <span>{{ card.amount }}</span>
            </div>
        </CardContent>
        <CardFooter class="flex gap-2 px-2 py-2 items-center justify-between">
            <div class="w-8 h-8 bg-neutral-100 rounded flex items-center justify-center">
                <Icon size="20" :name="card.icon" color="black"></Icon>
            </div>
            <p class="text-xs grow">{{ card.description }}</p>
            <Button variant="outline">{{ card.lable }}</Button>
        </CardFooter>
    </Card>
</template>

<script setup lang="ts">
    import { Badge } from "@/components/ui/badge"
    import {
        Card,
        CardContent,
        CardDescription,
        CardFooter,
        CardHeader,
        CardTitle,
    } from '@/components/ui/card'
    const props = defineProps(["card"]);
</script>

<style scoped>

</style>