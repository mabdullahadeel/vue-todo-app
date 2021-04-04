<template>
  <button class="btn" :style="{ background: color }">{{ buttonText }}</button>
</template>

<script>
export default {
  name: "Button",
  props: {
    buttonText: String,
    color: String,
  },
};
</script>

<style scoped>
.btn {
  display: inline-block;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>