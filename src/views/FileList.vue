<template>
  <list :list="list">
  </list>
</template>

<script>
import List from '../components/List'
// import fs from 'fs'

export default {
  name: 'Home',
  components: {
    List
  },

  data: () => ({
    list: []
  }),

  created () {
    // const defaultPath = '~/Desktop'
    // console.log('fileList ==>> ', fs.readdirSync)
    // const result = fs.readdirSync(defaultPath)
    // console.log(result)
  }
}
</script>
