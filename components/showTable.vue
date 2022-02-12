<template >
  <div style="margin-top: 30px">
    <vs-row>
      <vs-col w="12">
        <Card :styleTitle="'justify-content: space-between'">
          <template #title>
            <div style="display: flex; align-items: center">
              <span class="material-icons-outlined"> view_list </span>
              <span class="text-icon">Assignment of Open Work Order</span>
            </div>
            <vs-button gradient warn>Start WO</vs-button>
          </template>
          <template #content>
            <vs-row>
              <vs-button
                flat
                success
                :active="active === 'list'"
                @click="onViwData('list')"
                ><span class="material-icons-outlined icon"> article </span>
                <span class="text-icon">List</span>
              </vs-button>
              <vs-button
                flat
                success
                :active="active === 'calendar'"
                @click="onViwData('calendar')"
                ><span class="material-icons-outlined icon">
                  calendar_today
                </span>
                <span class="text-icon">Calendar</span>
              </vs-button>
              <vs-button
                flat
                success
                :active="active === 'user'"
                @click="onViwData('user')"
              >
                <span class="material-icons-outlined icon"> person </span>
                <span class="text-icon">Users</span>
              </vs-button>
            </vs-row>
            <vs-row>
              <vs-col w="12">
                <Table v-if="active === 'list'" :dataItems="dataItems"></Table>
                <Calendar
                  v-else-if="active === 'calendar'"
                  :totalTask="totalTask"
                ></Calendar>
              </vs-col>
            </vs-row>
          </template>
        </Card>
      </vs-col>
    </vs-row>
  </div>
</template>
<script >
import Card from "./card.vue";
import Table from "./tableList.vue";
import Calendar from "./calendar.vue";
import Vue from "vue";
import Moment from "moment";
export default Vue.extend({
  components: { Card, Table, Calendar },
  data() {
    return {
      active: "list",
      dataItems: [],
      totalTask: 0,
    };
  },
  mounted() {
    this.fetchData();
  },
  methods: {
    async fetchData() {
      const loading = this.$vs.loading();
      const res = await this.$axios.get(
        "https://swdapi.ddns.net:8090/data/ttntest"
      );
      this.totalTask = res.data.length;
      this.dataItems = res.data.map((e) => {
        return {
          ...e,
          dateGroup: e.timestamp ? Moment().format("DD/MM/YYYY") : "",
          showDate: e.timestamp ? Moment().format("DD/MM/YYYY HH:mm:ss") : "",
        };
      });
      console.log("is res", this.dataItems);
      loading.close();
    },
    onViwData(data) {
      this.active = data;
    },
  },
});
</script>
<style scoped>
</style>