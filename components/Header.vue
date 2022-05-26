<template>
  <div class="headerDiv">
    <img class="headerIcon" src="../assets/icon/list.svg" />
    <div class="headerTitle">HandsUP</div>
    <img class="headerIcon" src="../assets/icon/logout.svg" />
  </div>
</template>

<script>
export default {};
</script>

<style>
.headerDiv {
  display: flex;
  background: #8dc8ff;
  width: 100%;
  height: 5rem;
}

.headerTitle {
  flex-grow: 1;
  font-size: 3.5rem;
  font-weight: bold;
  color: white;
  
  text-overflow: ellipsis;
  white-space: nowrap;
  overflow: hidden;
}

.headerIcon {
  width: 4.5rem;
  padding:1rem;
  cursor: pointer;
}
</style>