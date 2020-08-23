<template>
  <div class="modal"></div>
</template>

<script>
export default {};
</script>

<style>
.modal {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 99;
  width: 700px;
  height: 300px;
  background-color: white;
  overflow: hidden;
  border: 1px solid black;
}

.slide-enter-active,
.slide-leave-active {
  transition: transform 0.5s;
}

.slide-enter,
.slide-leave-to {
  transform: translateY(-50%) translateX(100vw);
}
</style>
