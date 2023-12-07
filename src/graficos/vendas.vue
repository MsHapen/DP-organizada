<template>
  <Bar id="my-chart-id" :options="chartOptions" :data="chartData" :Title="chartTitle" />
</template>

<script>
import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

export default {
  components: { Bar },
  data() {
    return {
      chartData: {
        labels: [ 'Jan', 'Fev', 'Mar', 'Abr', 'Mai', 'Jun', 'Jul', 'Ago', 'Set' , 'Out', 'Nov', 'Dez' ],
        datasets: [ {
          label:'Vendas do Mês',
          data: [40, 20, 12, 10, 12, 92, 12, 9, 10, 50, 70 , 12],
          backgroundColor: '#FFD966', 
        } ],
      },
      chartOptions: {
        responsive: true,
      }
    }
  }
}
</script>
