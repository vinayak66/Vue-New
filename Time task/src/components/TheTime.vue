<template>
  <div class="in-lines">
    <input
      type="number"
      v-model.number="entertime"
      @focusout="addTime"
      style="width: 100px; height: 45px"
    />
    <!-- <button @click="addTime">Submit</button> -->
    <p  style="margin-left: 50px">
      Total Time:{{ updatingTime }}
    </p>
  </div>
</template>
<script>
export default {
  props: ["index", "Totaltime"],
  data() {
    return {
      entertime: 0,
      updatingTime:this.Totaltime,
    };
  },
  methods: {
    addTime() {
      this.updatingTime = this.updatingTime + this.entertime;
      this.$emit("save-time", this.updatingTime,this.index);
    },
  },
};
</script>
<style>
.in-lines {
  display: flex;
}
</style>