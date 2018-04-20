<template>
  <div id="editor">
    <nav>
      <ol>
        <li v-for="i in [0, 1, 2, 3, 4, 5, 6]" 
            v-bind:class="{active: currentTab === i}" 
            v-on:click="currentTab = i"
        >
          <svg class="icon">
            <use v-bind:xlink:href="`#icon-${icons[i]}`" fill: white></use>
          </svg>
        </li>
      </ol>
    </nav>
    <ol class="panes">
      <li v-bind:class="{active: currentTab === 0}">
        <ProfileEditor v-bind:profile="profile"/>
      </li>
      <li v-bind:class="{active: currentTab === 1}">
        <workExperienceEditor v-bind:workExperience="workExperience"/>
      </li>
      <li v-bind:class="{active: currentTab === 2}">
        <h2>学习经历</h2>
      </li>
      <li v-bind:class="{active: currentTab === 3}">
        <h2>兴趣爱好</h2>
      </li>
      <li v-bind:class="{active: currentTab === 4}">
        <h2>获得奖项</h2>
      </li>
      <li v-bind:class="{active: currentTab === 5}">
        <h2>项目经历</h2>
      </li>
      <li v-bind:class="{active: currentTab === 6}">
        <h2>联系方式</h2>
      </li>
    </ol>
  </div>
</template>

<script>
  import ProfileEditor from './ProfileEditor'
  import workExperienceEditor from './workExperienceEditor'
  export default {
    components: { ProfileEditor, workExperienceEditor },
    data(){
      return {
        currentTab: 0,
        icons: ['shenfenzheng', 'gongwenbao', 'book', 'xingquaihao--', 'jiangbei', 'project', 'cansaitubiaozhuanqu-'],
        profile: {
          name: '',
          city: '',
          birth: ''
        },
        workExperience: [
          {company: '', content: ''}
        ]
      }
    },
    methods:{

    },
    created(){
    }
  }
</script>

<style lang="scss">
  #editor {
    min-height: 100px;
    display: flex;
    > nav {
      display: flex;
      flex-direction: column;
      justify-content: space-around;
      background: #404347;
      width: 80px;
      
      >ol > li {
        margin: 0 5px 15px 5px;
        padding: 7px 0;
        text-align: center;
        border-radius: 4px;
        background: #404347;
        box-shadow: 0 0 10px hsla(0, 0, 0, 0.5);
        cursor: pointer;
        transition: all 0.5s;
        > .icon {
          width: 35px;
          height: 35px;
        } 
        &.active {
          padding: 13px 0;
          background: white;
          margin: 0 0 15px 0;
        }
      }
      >ol > li:nth-child(7) {
        margin-bottom: 0px;
      }
    }
    > .panes {
      flex: 1;
      .i-ct {
        position: relative;
        .el-icon-remove {
          font-size: 25px;
          color: #42444a;
          position: absolute;
          right: 0;
          top: 0;
          cursor: pointer;
        }
      }
      > li{
        display: none;
        padding: 25px;
        overflow: auto;
        height: 100%;
        &.active {
          display: block;
        }
      }
    }
  }
</style>
