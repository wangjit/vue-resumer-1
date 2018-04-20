<template>
  <div id="topbar">
    <div class="logo">
      Vue-Resumer
    </div>
    <div class="actions">
      <button type="button" class="btn btn-light">log up</button>
      <button type="button" class="btn btn-info">log in</button>
      <button type="button" class="btn btn-warning" v-on:click="preview">preview</button>
    </div>
  </div>
</template>

<style lang="scss">
  #topbar {
    display: flex;
    justify-content: space-between;
    align-items: 20px;
    padding: 16px;
    color: #fed136;
    background-color: #42444a;
    font-size: 2.5em;
    .logo {
      font-family: "Kaushan Script", "Helvetica Neue", Helvetica, Arial, cursive;
    }
  }
</style>
<script>
  export default {
    methods:{
      preview(){
        this.$emit('preview')
      }
    }
  }
</script>