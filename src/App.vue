<template>
<div id="app" v-bind:class="{previewMode: previewMode}">
  <Topbar class="topbar" v-on:preview="preview" />
  <main>
    <Editor v-bind:resume="resume" class="editor" />
    <preview v-bind:resume="resume" class="preview" />
  </main>
  <button type="button" class="btn btn-secondary" id="exitPreview" v-on:click="exitPreview" v-bind:btText="'exit'">Exit</button>
</div>
</template>

<script>
import Topbar from './components/Topbar'
import Editor from './components/Editor'
import Preview from './components/Preview'

export default {
  data() {
    return {
      previewMode: false,
      resume: {
        profile: {
          name: '',
          city: '',
          birth: ''
        },
        workExperience: [{
          company: '',
          content: ''
        }],
        studyExperience: [{
          school: '',
          duration: '',
          degree: ''
        }],
        likes: [{
          likes: '',
          detail: ''
        }],
        awards: [{
          awards: '',
          detail: ''
        }],
        projects: [{
          project: '',
          detail: ''
        }],
        contact: [{
          QQ: '',
          Wechat: '',
          Email: '',
          Phone: ''
        }]
      }
    }
  },
  methods: {
    exitPreview() {
      this.previewMode = false
    },
    preview() {
      this.previewMode = true
    }
  },
  components: {
    Topbar,
    Editor,
    Preview
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  height: 100vh;
  display: flex;
  flex-direction: column;
}

.topbar {
  position: relative;
  z-index: 1;
  box-shadow: 0 0 3px hsla(0, 0, 0, 0.5);
}

.icon {
  width: 1em;
  height: 1em;
  vertical-align: -0.15em;
  fill: currentColor;
  overflow: hidden;
}

main {
  display: flex;
  flex: 1;
  background: #DDD;
  >.editor {
    flex: 1;
    width: 40em;
    margin: 16px 8px 16px 16px;
    background: white;
    box-shadow: 0 0 3px hsla(0, 0, 0, 0.5);
    border-radius: 4px;
  }
  >.preview {
    flex: 1;
    padding: 0 20px;
    margin: 16px 16px 16px 8px;
    background: white;
    box-shadow: 0 0 3px hsla(0, 0, 0, 0.5);
    border-radius: 4px;
    overflow: hidden;
    word-wrap: break-word;
  }
}

.previewMode>#topbar {
  display: none;
}

.previewMode #editor {
  display: none;
}

.previewMode .preview {
  max-width: 800px;
  margin: 32px auto;
  overflow: hidden;
}

#exitPreview {
  display: none;
}

.previewMode #exitPreview {
  display: inline-block;
  position: fixed;
  right: 25px;
  top: 25px;
}
</style>
