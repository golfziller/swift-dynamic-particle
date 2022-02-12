<template>
  <div class="card">
    <div class="card-title" :style="styleTitle">
      <slot name="title"></slot>
    </div>
    <div class="card-body">
      <slot name="content"></slot>
    </div>
  </div>
</template>
<script >
export default {
  props: {
    styleTitle: String
  }
};
</script>
<style scoped>
.card-title {
  display: flex;
  align-items: center;
  padding: 13px;
  color: white;
  background-color: rgb(23, 201, 100);
}
.card-body {
  padding: 15px;
}
.card {
  border-radius: 5px;
  box-shadow: 1px 0px 7px 1px #888888;
}
</style>