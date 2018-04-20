<template>
  <div id="topbar">
    <div class="logo">
      Vue-Resumer
    </div>
    <div class="actions">
      <el-button type="primary" plain>注册</el-button>
      <el-button plain>登陆</el-button>
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
