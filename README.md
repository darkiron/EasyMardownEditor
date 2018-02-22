# EasyMarkdownEditor

## Description 

Simple Markdown editor for vuejs

## Demo

[try on codesandbox](https://codesandbox.io/s/kklm9zkzn3)

## Getting Started :

### installation

run :`npm i -D easymarkdowneditor`

### use

import the component from node-module:

```javascript
 import editor from 'easymarkdowneditor/easymarkdown'

 // Global registration :
 Vue.component('markdown-editor', editor)

 // In component : 
 app = Vue.extend({
  ...
  components: {
    'markdown-editor': editor
  },
  ...
  })
  ```

  and use `<markdown-editor>` directive in your form template : 

  ```html
   <markdown-editor v-model="data" ></markdown-editor>
  ```

### About :

#### Version 

1.0.2

#### Dependency

Font-awesome

#### Liscence 

MIT 
