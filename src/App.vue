<template>
  <!-- <div>
    <file-list></file-list>
    <textarea ref="code" class="code-area">
    </textarea>
  </div> -->
  <v-app id="inspire">
    <v-navigation-drawer
      v-model="drawer"
      app
      clipped
    >
      <v-list dense>
        <v-list-item link>
          <v-list-item-action>
            <v-icon>mdi-view-dashboard</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Dashboard</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item link>
          <v-list-item-action>
            <v-icon>mdi-cog</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Settings</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
      app
      clipped-left
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>Application</v-toolbar-title>
    </v-app-bar>

    <v-main>
      <textarea ref="code" class="code-area">
      </textarea>
    </v-main>

    <v-footer app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
// import HelloWorld from './components/HelloWorld'
// import { dialog } from 'electron'
// const electron = window.require('electron')
// const dialog = electron.remote.dialog
// const shell = electron.shell
import 'codemirror/mode/javascript/javascript.js'
import CodeMirror from 'codemirror'
// import FileList from './views/FileList'
const fs = window.require('fs')

export default {
  name: 'App',

  // components: {
  //   FileList
  // },

  data: () => ({
    myCodeMirror: null,
    drawer: null
  }),

  created () {
    this.$vuetify.theme.dark = true
    const result = fs.readdirSync('/Users/ide')
    console.log(result)
  },

  mounted () {
    this.myCodeMirror = CodeMirror.fromTextArea(this.$refs.code, {
      lineNumbers: true,
      tabSize: 2,
      mode: 'javascript',
      theme: '3024-night',
      value: ''
    })
    document.addEventListener('drop', (e) => {
      e.preventDefault()
      e.stopPropagation()

      for (const f of e.dataTransfer.files) {
        console.log('여기에 끌어다 둔 파일: ', f.path)
      }
    })
    document.addEventListener('dragover', (e) => {
      e.preventDefault()
      e.stopPropagation()
    })
  },

  methods: {
    onClick () {
      // shell.openExternal('https://github.com')
      // console.log('click', dialog)
      // const result = dialog.showOpenDialogSync({ properties: ['openFile', 'multiSelections'] })
      // console.log(result)
    }
  }
}
</script>
<style>
@import '../node_modules/codemirror/lib/codemirror.css';
@import '../node_modules/codemirror/theme/3024-night.css';
button {
  background: rgb(170, 141, 141) !important;
  width: 100px;
  height: 100px;
}

.CodeMirror {
  width: 100%;
  height: 100%;
}
</style>
