<template>
  <div>
    <vs-row justify="center">
      <vs-col lg="3" sm="6" xs="12">
        <Card>
          <template #title>
            <span class="material-icons-outlined"> task </span>
            <span class="text-icon">Totask in day</span>
          </template>
          <template #content>
            <div class="show-info">
              {{ totalTask.toLocaleString() }}
            </div>
          </template>
        </Card>
      </vs-col>
    </vs-row>
  
  </div>
</template>

<script>
import Card from "@/components/card";
export default {
  components: { Card },
  props: {
    totalTask: {
      type: Number,
      requried: true,
    },
  },
};
</script>

<style>
</style>