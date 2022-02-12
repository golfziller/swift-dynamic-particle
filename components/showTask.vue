<template>
     <div class="center grid">
      <vs-row >
        <vs-col vs-type="flex" vs-justify="center" vs-align="center" lg="2" sm="4" xs="12"  v-for="(item,index) in dataTask" :key="index">
          <Card>
            <template #title>
              <span class="material-icons-outlined" > {{item.icon}} </span> <span class="text-icon">{{item.name}}</span>
            </template>
            <template #content>
              <div class="show-info">
                {{item.value}}
              </div>
            </template>
          </Card>
        </vs-col>
      </vs-row>
      <vs-row></vs-row>
    </div>
</template>
<script>
import Card from "@/components/card";
export default {
  components: { Card },
  data() {
    return {
      dataTask: [
        {
          icon: 'info',
          name: 'Upcoming Task',
          value: 1
        },
        {
          icon: 'alarm_add',
          name: 'Late Task',
          value: 5
        },
        {
          icon: 'swap_horiz',
          name: 'Open Task',
          value: 0
        },
        {
          icon: 'done',
          name: 'Complete Task',
          value: 1
        },
        {
          icon: 'alarm_on',
          name: 'Overdue Task',
          value: 2
        },
        {
          icon: 'alarm',
          name: 'Time Spent',
          value: '24 hr'
        },
        
      ]
    }
  }
};
</script>
<style>
.show-info {
  display:flex;
  align-items: center;
  justify-content: center;
  font-size: 40px;
  height: 100px
}

</style>