<template>
<div>
  <h2>{{title}}</h2>
  <el-form>
    <div class="i-ct" v-for="(item, index) in items" v-bind:key="index">
      <el-form-item v-for="key in keys" v-bind:label="labels[key] || key" v-bind:key="key">
        <el-input v-model="item[key]"></el-input>
      </el-form-item>
      <button type="button" class="btn btn-secondary btn-sm" v-if="items.length > 1" v-on:click="removeItem(index)">删除第{{index + 1}}项</button>
      <hr style="margin-bottom: 10px; ">
    </div>
    <button type="button" class="btn btn-primary btn-sm" v-on:click="addItem">添加一项</button>
  </el-form>
</div>
</template>

<script>
export default {
  props: ['items', 'labels', 'title'],
  computed: {
    keys(){
      return Object.keys(this.items[0])
    }
  },
  methods: {
    addItem() {
      const empty = {}
      this.keys.map((key)=>{
        empty[key] = ''
      })
      this.items.push(empty)
    },
    removeItem(index) {
        this.items.splice(index, 1)
    }
  }
}
</script>
