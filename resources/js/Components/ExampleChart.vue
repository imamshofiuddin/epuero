<template>
    <line-chart :chartData="testData" class="h-60 w-full"/>
</template>

<script>
import { defineComponent } from 'vue';
import { LineChart } from 'vue-chart-3';
import { Chart, registerables } from "chart.js";

Chart.register(...registerables);

export default defineComponent({
    name: 'Home',
    components: { LineChart },
    setup() {
        const testData = {
            labels: ['Paris', 'Nîmes', 'Toulon', 'Perpignan', 'Autre'],
            datasets: [
                {
                    data: [30, 40, 60, 70, 5],
                    backgroundColor: ['#77CEFF', '#0079AF', '#123E6B', '#97B0C4', '#A5C8ED'],
                },
            ],
        };

        return { testData };
    },
});
</script>
