<template>
  <div id="preview">
    <h1>{{resume.profile.name || '请填写姓名'}}</h1>
    <p>{{resume.profile.city || '请填写城市'}} | {{resume.profile.birth || '请填写出生年月'}}</p>
    <hr>
    <section v-if="filter(resume.workExperience).length > 0">
      <h2>工作经历</h2>
      <ul>
        <li v-for="item in filter(resume.workExperience)">
          {{item.company}}
          {{item.content}}
        </li>
      </ul>
    </section>
    <section v-if="filter(resume.studyExperience).length > 0">
      <h2>学习经历</h2>
      <ul>
        <li v-for="item in filter(resume.studyExperience)">
          {{item.school}}
          {{item.duration}}
          {{item.degree}}
        </li>
      </ul>
    </section>
    <section v-if="filter(resume.likes).length > 0">
      <h2>兴趣爱好</h2>
      <ul>
        <li v-for="item in filter(resume.likes)">
          {{item.likes}}
          {{item.detail}}
        </li>
      </ul>
    </section>
    <section v-if="filter(resume.awards).length > 0">
      <h2>获得奖项</h2>
      <ul>
        <li v-for="item in filter(resume.awards)">
          {{item.awards}}
          {{item.detail}}
        </li>
      </ul>
    </section>
    <section v-if="filter(resume.projects).length > 0">
      <h2>项目经历</h2>
      <ul>
        <li v-for="item in filter(resume.projects)">
          {{item.project}}
          {{item.detail}}
        </li>
      </ul>
    </section>
    <section v-if="filter(resume.contact).length > 0">
      <h2>联系方式</h2>
      <ul>
        <li v-for="item in filter(resume.contact)">
          {{item.QQ}}
          {{item.Wechat}}
          {{item.Email}}
          {{item.Phone}}
        </li>
      </ul>
    </section>
  </div>
</template>

<style>
  #preview {
    min-height: 100px;
  }
</style>

<script>
  export default {
    props: ['resume'],
    methods: {
      filter(array){ //找出非空对象
        return array.filter(item=> !this.isEmpty(item))
      },
      isEmpty(object){//只要有一个value不是empty,就返回false
        let empty = true
        for(let key in object){
          if(object[key]){
            empty = false
            break
          }
        }
        return empty
      }
    }
  }
</script>