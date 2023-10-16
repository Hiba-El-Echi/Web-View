<template>
  <div class="add-container">
    <div class="add">
      <img src="../assets/img/add.svg" />
    </div>
  </div>
</template>
<script setup>

</script>
<style lang="scss" scoped>
.add-container {
  display: flex;
  justify-content: flex-end;
  margin-top: 200px;
  .add {
    background-color: #000;
    border-radius: 100px;
    box-shadow: 0px 1px 3px 0px rgba(0, 0, 0, 0.3),
      0px 4px 8px 3px rgba(0, 0, 0, 0.15);
    height: 60px;
    width: 60px;
    display: flex;
    align-items: center;
    justify-content: center;
  }
}
</style>
