<template>
  <div id="top-nav">
    <div class="nav-left">
      logo
    </div>
    <div class="nav-right">
      nav
    </div>
  </div>
</template>
<script setup>
</script>
<style scoped>
#top-nav {
  box-sizing: border-box;
  width: 100%;
  height: 70px;
  position: fixed;
  top: 0;
  z-index: 9999;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-left: 100px;
  padding-right: 100px;
  /* background-color: rgba(0, 0, 0, .3); */
}

.nav-left,
.nav-right {
  font-size: 30rem;
  font-weight: 600;
  color: #fff;
}
</style>