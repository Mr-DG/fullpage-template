<template>
  <div class="main">
    <TopNav />
    <Control :currentIndex="currentIndex" />
    <Section1 :class="{
      active: currentIndex == 0,
      preActive: prevIndex == 0,
      sectionMoveFromTop: !direction && currentIndex == 0,
    }" />
    <Section2 :class="{
      active: currentIndex == 1,
      preActive: prevIndex == 1,
      sectionMoveFromBottom: direction && currentIndex == 1,
      sectionMoveFromTop: !direction && currentIndex == 1
    }" />
    <Section3 :class="{
      active: currentIndex == 2,
      preActive: prevIndex == 2,
      sectionMoveFromBottom: direction && currentIndex == 2,
      sectionMoveFromTop: !direction && currentIndex == 2
    }" />
    <Section4 :class="{
      active: currentIndex == 3,
      preActive: prevIndex == 3,
      sectionMoveFromBottom: direction && currentIndex == 3,
      sectionMoveFromTop: !direction && currentIndex == 3
    }" />
    <Section5 :class="{
      active: currentIndex == 4,
      preActive: prevIndex == 4,
      sectionMoveFromBottom: direction && currentIndex == 4,
      sectionMoveFromTop: !direction && currentIndex == 4
    }" />
    <Section6 :class="{
      active: currentIndex == 5,
      preActive: prevIndex == 5,
      sectionMoveFromBottom: direction && currentIndex == 5,
      sectionMoveFromTop: !direction && currentIndex == 5
    }" />
    <Section7 :class="{
      active: currentIndex == 6,
      preActive: prevIndex == 6,
      sectionMoveFromBottom: direction && currentIndex == 6,
      sectionMoveFromTop: !direction && currentIndex == 6
    }" />
    <Section8 :class="{
      active: currentIndex == 7,
      preActive: prevIndex == 7,
      sectionMoveFromBottom: currentIndex == 7
    }" />
    <Footer />
  </div>
</template>
<script setup>
import { onMounted, onUnmounted, ref } from 'vue'
import Footer from '../../components/Footer.vue'
import TopNav from '../../components/TopNav.vue'
import Control from './Control.vue'
import Section1 from './Section1.vue'
import Section2 from './Section2.vue'
import Section3 from './Section3.vue'
import Section4 from './Section4.vue'
import Section5 from './Section5.vue'
import Section6 from './Section6.vue'
import Section7 from './Section7.vue'
import Section8 from './Section8.vue'
const section = document.getElementsByClassName('section')
const pageUlLi = document.getElementsByClassName('pageUlLi')
const footer = document.getElementsByClassName('footer')
// ????????????section
const currentIndex = ref(0)
// ?????????section
const prevIndex = ref()
// ????????????????????????????????????
const direction = ref(true)
// ???????????????????????????
const isClick = ref(false)
// ??????footer????????????
const isFooterShow = ref(false)

// ??????section
const toSection = (index) => {
  if (isClick.value) {
    prevIndex.value = currentIndex.value
    isClick.value = false
    footer[0].classList.remove('isFooterShow')
    isFooterShow.value = false
  }
  currentIndex.value = index
}

// ??????????????????
const upFn = () => {
  direction.value = false
  // ????????????
  // ??????????????????section?????????????????????
  if (currentIndex.value === 0) {
    return
  }
  if (currentIndex.value === section.length - 1) {
    // ??????footer?????????????????????????????????footer
    if (isFooterShow.value) {
      setTimeout(function () {
        footer[0].classList.remove('isFooterShow')
      }, 700)
      section[currentIndex.value].classList.remove('footer-hide')
      section[currentIndex.value].classList.add('footer-hide')
      isFooterShow.value = false
      return
    }
  }
  prevIndex.value = currentIndex.value
  currentIndex.value--
  toSection(currentIndex.value)
}
// ??????????????????
const downFn = () => {
  direction.value = true
  // ????????????
  // ?????????????????????section?????????????????????
  if (currentIndex.value === 7) {
    isFooterShow.value = true
    // ???footer??????visibility??????
    footer[0].classList.add('isFooterShow')
    // ???????????????section??????class
    section[currentIndex.value].classList.remove('footer-hide')
    section[currentIndex.value].classList.add('footer-show')
    return
  }
  prevIndex.value = currentIndex.value
  currentIndex.value++
  toSection(currentIndex.value)
}
// ????????????????????????
const scrollFunc = (e) => {
  if (e.wheelDelta > 0) {
    upFn()
  } else {
    downFn()
  }
}

onMounted(() => {
  for (let i = 0; i < pageUlLi.length; i++) {
    pageUlLi[i].addEventListener('click', () => {
      isClick.value = true
      toSection(i)
    })
  }
})

// ??????????????????
const destroyScroll = () => {
  window.removeEventListener('mousewheel', a)
}
onUnmounted(() => {
  destroyScroll()
})

// ????????????
function throttle(fn, delay) {
  let activeTime = 0
  return function () {
    const currentTime = Date.now()
    // ??????????????????????????????????????????????????????delay???????????????fn
    if (currentTime - activeTime > delay) {
      fn.apply(this, arguments)
      activeTime = Date.now()
    }
  }
}
// ????????????????????????
const a = throttle(scrollFunc, 700)
window.addEventListener('mousewheel', a)

//////////////////////////////////////
/////////// ?????????????????????//////////////
//////////////////////////////////////
const touch = () => {
  let startPageY
  let endPageY
  const touchMove = (e) => {
    endPageY = e.changedTouches[0].pageY
    if (startPageY - endPageY > 0) {
      downFn()
    } else if (startPageY - endPageY < 0) {
      upFn()
    } else {
      console.log('?????????')
    }
  }
  const b = throttle(touchMove, 700)
  // ????????????????????????pageY
  window.addEventListener('touchstart', function (e) {
    startPageY = e.changedTouches[0].pageY
  })
  // ??????????????????
  window.addEventListener('touchmove', b, false)
}
touch()

</script>
<style scoped>
.main {
  width: 100%;
  height: 100%;
  position: relative;
}

.section {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  z-index: 10;
}

.active {
  z-index: 999;
}

.preActive {
  z-index: 99;
}

.isFooterShow {
  visibility: visible;
}

/* ?????? */
/* page?????????????????? */
.sectionMoveFromBottom {
  animation: moveFromBottom 0.65s cubic-bezier(0.45, 0.05, 0.55, 0.95);
}

@keyframes moveFromBottom {
  from {
    -webkit-transform: translate3d(0%, 100%, 1px) scale(0.75, 1);
  }

  to {
    -webkit-transform: translate3d(0%, 0%, 1px) scale(1, 1);
  }
}

/* page?????????????????? */
.sectionMoveFromTop {
  transform-origin: top;
  -webkit-animation: moveFromTop 0.65s cubic-bezier(0.45, 0.05, 0.55, 0.95);
  animation: moveFromTop 0.65s cubic-bezier(0.45, 0.05, 0.55, 0.95);
}

@keyframes moveFromTop {
  from {
    -webkit-transform: translate3d(0%, -100%, 1px) scale(0.75, 1);
  }

  to {
    -webkit-transform: translate3d(0%, 0%, 1px) scale(1, 1);
  }
}

/* footer???????????? */
.footer-show {
  transform: translateY(-414rem);
  -webkit-animation: showFooter 0.4s cubic-bezier(0.45, 0.05, 0.55, 0.95);
  animation: showFooter 0.4s cubic-bezier(0.45, 0.05, 0.55, 0.95);
}

@keyframes showFooter {
  from {
    -webkit-transform: translateY(0px);
  }

  to {
    -webkit-transform: translateY(-414rem);
  }
}

/* footer???????????? */
.footer-hide {
  transform: translateY(0px);
  -webkit-animation: hideFooter 0.4s cubic-bezier(0.45, 0.05, 0.55, 0.95);
  animation: hideFooter 0.4s cubic-bezier(0.45, 0.05, 0.55, 0.95);
}

@keyframes hideFooter {
  from {
    transform: translateY(-414rem);
  }

  to {
    transform: translateY(0px);
  }
}
</style>