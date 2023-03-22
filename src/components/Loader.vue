<template>
  <div class="loader">
    <span></span>
    <span></span>
    <span></span>
  </div>
</template>

<script>
export default {
  name: 'TheLoader'
}
</script>

<style scoped>
.loader {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);  /* выровнять по центру обьект */
    width: 150px;
    height: 150px;
    /* background: #0c1025; */
}

.loader span {
    position: fixed;
    width: 50px;
    height: 50px;
    background: #fff;
    border-radius: 4px;
    animation: animate 2s linear infinite;
}

.loader span:nth-child(1) {
    animation-delay: 0s;
    background: #fd3f39;
}

.loader span:nth-child(2) {
    animation-delay: -0.667s;
    background: #ffcb2f
}
.loader span:nth-child(3) {
    animation-delay: -1.33s;
    background: #53d86a;
}

@keyframes animate {
  0% {
    top: 0;
    left: 0;
  }
  12.5% {
    top: 0;
    left: 50%;
  }
  25% {
    top: 0;
    left: 50%;
  }
  37.5% {
    top: 50%;
    left: 50%;
  }
  50% {
    top: 50%;
    left: 50%;
  }
  62.5% {
    top: 50%;
    left: 0;
  }
  75% {
    top: 50%;
    left: 0;
  }
  87.5% {
    top: 0;
    left: 0;
  }
  100% {
    top: 0;
    left: 0;
  }
}
</style>
