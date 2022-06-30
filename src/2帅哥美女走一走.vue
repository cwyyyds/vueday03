<template>
  <div>
    <ul v-for="item in arr" :key="item">
      <li>{{ item }}</li>
    </ul>
    <button @click="clickFn">换位</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      arr: ['帅哥', '美女', '程序员'],
    }
  },
  methods: {
    clickFn() {
      this.arr.push(this.arr[0])
      this.arr.shift()
    },
  },
}
</script>

<style></style>
