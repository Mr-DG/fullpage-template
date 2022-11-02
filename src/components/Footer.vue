<template>
  <div class="footer">
    <div class="footer-box">
      <div class="footer-top">
        <div class="top-1">
          <div>CONTACT US</div>
          <div>Mail：xxxx.cn</div>
          <div>Telephone：+86-755-233535352</div>
        </div>
        <div class="top-2">ETM Technology</div>
        <div class="top-3">
        </div>
      </div>
      <div class="footer-bottom">
        <div class="bottom-left">© 2021 . All rights reserved.</div>
        <div class="bottom-right">
          <span>Terms of use</span>
          <span>Privacy Policy</span>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>

</script>
<style scoped>
.footer {
  width: 100%;
  height: 414rem;
  position: absolute;
  top: 0;
  z-index: 99;
  margin-top: calc(100vh - 414rem);
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  visibility: hidden;
  background-color: #fff;
}

.footer-box {
  max-width: 1600rem;
  margin: 0 auto;
}

.top-1 {
  display: flex;
  align-items: center;
  margin-top: 67rem;
  margin-bottom: 17rem;
}

.top-1 div:nth-child(1) {
  font-family: 'myFont5';
  font-weight: 900;
  font-size: 80rem;
  color: #212121;
  margin-right: 69rem;
}

.top-1 div:nth-child(2),
.top-1 div:nth-child(3) {
  font-size: 16rem;
  color: #333333;
  margin-right: 69rem;
  font-weight: 700;
}

.top-2 {
  font-size: 24rem;
  color: #232323;
  margin-bottom: 20rem;
  font-weight: 700;
}

.top-3 {
  display: flex;
}

.top-3 img {
  width: 35rem;
  height: 35rem;
  cursor: pointer;
}

.top-3 img {
  margin-right: 27rem;
}

.footer-top {
  box-sizing: border-box;
  height: 290rem;
}

.footer-bottom {
  display: flex;
  justify-content: space-between;
  border-top: 1px solid #8D929E;
  padding: 16rem 0;
  font-size: 16rem;
  color: #333333;
}

.bottom-right span:nth-child(1) {
  margin-right: 20rem;
}
</style>