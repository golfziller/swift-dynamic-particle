
<template>
  <div>
    <vs-row justify="space-between">
      <h4>Table List</h4>
      <vs-button info size="small" @click="onShowGraph">
        <span class="text-icon">Analytics</span>
        <template #animate>
          <span class="material-icons"> analytics </span>
        </template>
      </vs-button>
    </vs-row>
    <vs-table>
      <template #thead>
        <vs-tr>
          <vs-th> Id </vs-th>
          <vs-th> Data </vs-th>
          <vs-th> Time Stamp </vs-th>
        </vs-tr>
      </template>
      <template #tbody>
        <vs-tr
          :key="i"
          v-for="(tr, i) in $vs.getPage(dataItems, page, max)"
          :data="tr"
        >
          <vs-td>
            {{ tr.id }}
          </vs-td>
          <vs-td>
            {{ tr.data }}
          </vs-td>
          <vs-td>
            {{ tr.showDate }}
          </vs-td>
        </vs-tr>
      </template>
      <template #footer>
        <vs-pagination v-model="page" :length="$vs.getLength(dataItems, max)" />
      </template>
    </vs-table>
    <DialogGraph
      :active="dialogOpen"
      @onClose="onClose"
      :dataGraph="dataGraph"
    ></DialogGraph>
  </div>
</template>
<script>
import DialogGraph from "./dialogGraph.vue";
import _ from "lodash";
export default {
  components: { DialogGraph },
  props: {
    dataItems: {
      type: Array,
      default: () => [],
    },
  },
  data: () => ({
    page: 1,
    max: 15,
    dialogOpen: false,
    dataGraph: {
      series: [],
      categories: [],
    },
  }),
  methods: {
    onShowGraph() {
      const gData = _.chain(this.dataItems)
        .groupBy("dateGroup")
        .map((value, key) => ({ key: key, data: value }))
        .value();
      console.log(gData);
      let dataCate = [];
      let dataSeries = [];
      gData.forEach((e) => {
        const maxData = _.maxBy(e.data, "data");
        const minData = _.minBy(e.data, "data");
        const avgData =  _.meanBy(e.data, "data").toFixed(2);
        dataSeries = [
          ...dataSeries,
          { name: "Max", data: [maxData.data] },
          { name: "Min", data: [minData.data] },
          { name: "Avg", data: [avgData] },
        ];
        dataCate = [...dataCate, e.key];
      });
      this.dataGraph = {
        series: dataSeries,
        categories: dataCate
      }
      this.dialogOpen = true;
    },
    onClose() {
      this.dialogOpen = false;
    },
  },
};
</script>

        