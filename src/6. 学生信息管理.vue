<template>
  <div id="app">
    <div>
      <span>姓名:</span>
      <input type="text" v-model="name" />
    </div>
    <div>
      <span>年龄:</span>
      <input type="number" v-model="age" />
    </div>
    <div>
      <span>性别:</span>
      <select v-model="sex">
        <option value="男">男</option>
        <option value="女">女</option>
      </select>
    </div>
    <div>
      <button @click="addFn">添加/修改</button>
    </div>
    <div>
      <table border="1" cellpadding="10" cellspacing="0">
        <tr>
          <th>序号</th>
          <th>姓名</th>
          <th>年龄</th>
          <th>性别</th>
          <th>操作</th>
        </tr>
        <tr v-for="item in arr" :key="item.id">
          <td>{{ item.id }}</td>
          <td>{{ item.name }}</td>
          <td>{{ item.age }}</td>
          <td>{{ item.sex }}</td>
          <td>
            <button @click="delFn(item.id)">删除</button>
            <button @click="ModifyThe(item.id)">编辑</button>
          </td>
        </tr>
      </table>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      arr: [],
      name: '',
      age: '',
      sex: '男',
      id: '',
    }
  },
  methods: {
    addFn() {
      if (this.name == '' || this.age == '' || this.sex == '') {
        return alert('不能为空')
      } else if (this.arr.findIndex((item) => item.id == this.id) !== -1) {
        console.log(1)
        this.$set(this.arr, this.arr[0])
        return
      }
      const id = this.arr[this.arr.length - 1]
        ? this.arr[this.arr.length - 1].id + 1
        : 1
      this.arr.push({
        id,
        name: this.name,
        age: this.age,
        sex: this.sex,
      })
    },
    delFn(id) {
      const index = this.arr.findIndex((item) => item.id == id)
      this.arr.splice(index, 1)
    },
    ModifyThe(id) {
      this.id = id
      const index = this.arr.findIndex((item) => item.id == id)
      this.$set(this.arr, index, {
        id: index + 1,
        name: this.name,
        age: this.age,
        sex: this.sex,
      })
    },
  },
}
</script>
<style>
tr td {
  border: 1px solid black;
}
</style>
