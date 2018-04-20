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
        <ProfileEditor v-bind:profile="resume.profile"/>
      </li>
      <li v-bind:class="{active: currentTab === 1}">
        <itemsEditor v-bind:items="resume.workExperience" v-bind:labels="{company: '公司', content: '工作内容'}" v-bind:title="'工作经历'"/>
      </li>
      <li v-bind:class="{active: currentTab === 2}">
        <itemsEditor v-bind:items="resume.studyExperience" v-bind:labels="{school: '学校', duration: '时间', degree: '学位'}" v-bind:title="'学习经历'"/>
      </li>
      <li v-bind:class="{active: currentTab === 3}">
        <itemsEditor v-bind:items="resume.likes" v-bind:labels="{likes: '我喜欢', detail: '关于我的兴趣'}" v-bind:title="'兴趣爱好'"/>
      </li>
      <li v-bind:class="{active: currentTab === 4}">
        <itemsEditor v-bind:items="resume.awards" v-bind:labels="{awards: '奖项名称', detail: '奖项描述'}" v-bind:title="'获得奖项'"/>
      </li>
      <li v-bind:class="{active: currentTab === 5}">
        <itemsEditor v-bind:items="resume.projects" v-bind:labels="{project: '项目名称', detail: '项目描述'}" v-bind:title="'项目经历'"/>
      </li>
      <li v-bind:class="{active: currentTab === 6}">
        <itemsEditor class="none" v-bind:items="resume.contact" v-bind:labels="{QQ: 'QQ', Wechat: '微信', Email: '邮箱', Phone: '手机'}" v-bind:title="'联系方式'"/>
      </li>
    </ol>
  </div>
</template>

<script>
  import ProfileEditor from './ProfileEditor'
  import itemsEditor from './itemsEditor'
  //import contactEditor from './contactEditor'
  export default {
    components: {
      ProfileEditor, 
      itemsEditor
    },
    props: ['resume'],

    data(){
      return {
        currentTab: 0,
        icons: [
          'shenfenzheng', 
          'gongwenbao', 
          'book', 
          'xingquaihao--', 
          'jiangbei', 
          'project', 
          'cansaitubiaozhuanqu-'
          ],
        profile: {
          name: '',
          city: '',
          birth: ''
        },
        workExperience: [
          {company: '', content: ''}
        ],
        studyExperience: [
          {
            school: '', duration: '', degree: ''
          }
        ],
        likes: [
          {
            likes: '', detail: ''
          }
        ],
        awards: [
          {
            awards: '', detail: ''
          }
        ],
        projects: [
          {
            project: '', detail: ''
          }
        ],
        contact: [
          {
            QQ: '', Wechat: '', Email: '', Phone: ''
          }
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
    overflow: hidden;
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
        .btn-secondary {
          position: absolute;
          right: 0;
          top: 0;
        }
      }
      > li {
        display: none;
        padding: 25px;
        overflow: auto;
        height: 100%;
        &.active {
          display: block;
        }
        .none {
          i {
            display: none;
          }
          button {
            display: none;
          }
          hr {
            display: none;
          }
        }
      }
    }
  }
</style>