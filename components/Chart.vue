<template>
    <div class="border p-4 rounded-lg">
        <highchart v-if="data.length > 0" :options="chartOptions" />
    </div>
</template>

<script setup lang="ts">
    let props = defineProps(["currentCategory", "data"])
    let data = props.data || []
    let currentCategory = props.currentCategory || "today"

    let categories = ref({
    'today': [
                "00:00", "01:00", "02:00", "03:00", "04:00", "05:00", "06:00", "07:00",
                "08:00", "09:00", "10:00", "11:00", "12:00", "13:00", "14:00", "15:00",
                "16:00", "17:00", "18:00", "19:00", "20:00", "21:00", "22:00", "23:00"
            ],
    'week': ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"],
    'year': ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"],
})

const chartOptions = computed(() => (
    {
        chart: {
            type: 'line',
            animation: {
                enabled: false
            }
        },
        legend: {
            enables: false
        },
        title: {
            text: ''
        },
        xAxis: {
            gridLineColor: 'transparent',
            categories: categories[currentCategory]
        },
        yAxis: {
            gridLineColor: 'transparent',
            title: {
                text: ''
            }
        },
        plotOptions: {
            line: {
                marker: {
                    enabled: false
                },
                dataLabels: {
                    enabled: false
                },
                enableMouseTracking: true
            }
        },
        series: [{
            name: 'line',
            lineWidth: '4px',
            color: {
                linearGradient: {},
                stops: [
                    [0, 'rgba(252, 176, 69, 1)'],
                    [0.33, 'rgba(253, 29, 29, 1)'],
                    [0.66, 'rgba(131, 58, 180, 1)'],
                    [1, 'rgba(29, 217, 83, 1)'],
                ]
            },
            data: data.value 
        }]
    }
))
</script>

<style scoped>

</style>