<template>
  <div class="login-container">
    <button @click="loginSubmit">Login con Google!</button>
  </div>
</template>

<script>
export default {
  methods: {
    loginSubmit() {
        this.$emit('input')
    }
  }
}
</script>


<style lang="scss">
  .login-container {
    width: 100%;
    text-align: center;
    padding-top: 50px;
    button {
      width: 50%;
      background-color: #4e37fc;
      color: white;
      font-weight: bold;
      font-size: 18pt;
      padding: 20px;
      border-radius: 15px;
      border: none;
      box-shadow: #00000040 0px 5px 10px;
      cursor: pointer;
      &:hover {
        background-color: #7562ff;
      }
    }
  }
</style>