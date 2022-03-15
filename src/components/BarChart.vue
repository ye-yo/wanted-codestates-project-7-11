<template>
  <BarChart
    v-bind="barChartProps"
    :style="{
      width: '15rem',
      height: '15rem',
      alignItems: 'center',
    }"
  />
</template>

<script>
import { computed, defineComponent, ref, toRefs } from "vue";
import { BarChart, useBarChart } from "vue-chart-3";
import { Chart, registerables } from "chart.js";

const dataChange = (data) => {
  let arr = [];
  data.forEach((element) =>
    element > 5 ? arr.push(-element) : arr.push(element)
  );
  return arr;
};

Chart.register(...registerables);

export default defineComponent({
  props: {
    user: {
      type: Number,
      required: true,
    },
    company: {
      type: Number,
      required: true,
    },
  },
  chartData: "BarProcess",
  components: { BarChart },
  setup(props) {
    const { user, company } = toRefs(props);
    console.log(user, company);
    const options = ref({
      barThickness: 10,
      responsive: true,
      indexAxis: "y",
      scales: {
        x: {
          display: false,
        },
        y: {
          display: false,
        },
      },
      plugins: {
        legend: false,
        tooltip: false,
      },
    });

    const chartData = computed(() => ({
      labels: ["", "", "", "", ""],
      datasets: [
        {
          data: dataChange(user.value),
          backgroundColor: "#6E3CF9",
        },
        {
          data: dataChange(company.value),
          backgroundColor: "#FFD966",
        },
      ],
    }));

    const { barChartProps, barChartRef } = useBarChart({
      chartData,
      options,
    });

    return { barChartProps, barChartRef };
  },
});
</script>
