# EasyMardownEditor

## Description 

Simple Markdown editor for vuejs

## Getting Started :

### installation

run :`npm -i easymarkdowneditor`

### use

import the component from node-module:

```javascript
 import editor from 'eastmarkdowneditor'

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

  and use `<editor>` directive in your form template : 

  ```html
   <markdown-editor v-model="data" ></markdown-editor>
  ```


### About :

### Version 

1.0.0

### Liscence 

MIT 
