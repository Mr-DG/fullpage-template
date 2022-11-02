<template>
  <ul id="sectionControl" type="none">
    <li id="pageUlLi1" class="pageUlLi" :class="{ activeLi: currentIndex == 0 }"></li>
    <li id="pageUlLi2" class="pageUlLi" :class="{ activeLi: currentIndex == 1 }"></li>
    <li id="pageUlLi3" class="pageUlLi" :class="{ activeLi: currentIndex == 2 }"></li>
    <li id="pageUlLi4" class="pageUlLi" :class="{ activeLi: currentIndex == 3 }"></li>
    <li id="pageUlLi5" class="pageUlLi" :class="{ activeLi: currentIndex == 4 }"></li>
    <li id="pageUlLi6" class="pageUlLi" :class="{ activeLi: currentIndex == 5 }"></li>
    <li id="pageUlLi7" class="pageUlLi" :class="{ activeLi: currentIndex == 6 }"></li>
    <li id="pageUlLi8" class="pageUlLi" :class="{ activeLi: currentIndex == 7 }"></li>
  </ul>
</template>
<script setup>
const { currentIndex } = defineProps(['currentIndex'])
</script>
<style scoped>
#sectionControl {
  position: fixed;
  right: 50px;
  top: 50%;
  transform: translateY(-50%);
  z-index: 9999;
}

.activeLi {
  height: 10px;
  border-width: 3px;
  border-color: #002fa7;
}

li {
  width: 20px;
  height: 10px;
  margin: 0 10px;
  cursor: pointer;
  margin: 20rem 0;
  border-top: 1px solid #666;
}
</style>