<!-- components/BarChart.vue -->

<template>
    <div>
      <apexchart type="bar" :options="chartOptions" :series="chartSeries" />
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        chartOptions: {
          chart: {
            type: 'bar',
          },
          xaxis: {
            categories: ['Jan', 'Feb', 'Mar', 'Apr', 'May'],
          },
        },
        chartSeries: [
          {
            name: 'Sales',
            data: [30, 40, 45, 50, 49],
          },
        ],
      };
    },
  };
  </script>
  