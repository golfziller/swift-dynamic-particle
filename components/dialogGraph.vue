<template>
  <vs-dialog overflow-hidden width="600px" v-model="modelActive" prevent-close @close="onClose">
    <apexchart type="bar" :options="dataOptions" :series="dataSeries"></apexchart>
  </vs-dialog>
</template>

<script>
export default {
  props: {
    active: Boolean,
    dataGraph: {
        type: Object,
    },
  },
  watch: {
      active: function(newVal) {
          this.modelActive = newVal
      },
      dataGraph: function(newVal) {
        this.dataSeries = [...newVal.series]
        this.dataOptions.xaxis.categories = [...newVal.categories]
      }
  },
  methods: {
    onClose() {
      this.$emit("onClose");
    },
  },
  created () {
      this.modelActive = this.active
      this.dataSeries = [...this.dataGraph.series]
      this.dataOptions.xaxis.categories = [...this.dataGraph.categories]
  },
  data() {
    return {
      modelActive: false,
      dataOptions: {
        chart: {
          id: "vuechart-example",
        },
        xaxis: {
          categories: [],
        },
      },
      dataSeries: [
        // {
        //   name: "series-1",
        //   data: [30, 40, 45, 50, 49, 60, 70, 91],
        // },
      ],
    };
  },
};
</script>

<style>
</style>