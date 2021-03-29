<template>
  <div class="modal">
    <div class="modal-content w-4/5 sm:w-1/3">

    <slot> </slot>
    </div>
  </div>
</template>

<script>
export default {
  name: "MovieInfo",

};
</script>

<style scoped>
.modal {
  position: fixed;
  z-index: 1;
  left: 0;
  top: 0;
  width: 100%; 
  height: 100%;
  background-color: rgb(0, 0, 0);
  background-color: rgba(0, 0, 0, 0.801);
}

.modal-content {
  position: absolute;
  background-color: #d6d6d6;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  padding: 20px;
  border: 5px solid rgb(0, 0, 0);
  border-radius: 10px;
}
</style>