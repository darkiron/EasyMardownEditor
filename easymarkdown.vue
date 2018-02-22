<template>
  <div class="container">
    <div class="toolbar">
      <toolbar-button v-for="button in buttons" @click="func" :tag="button.tag" :before="button.before" :after="button.after" :icone="button.icone" >
      </toolbar-button>

    </div>
    <textarea class="editor" @input="send" :value="value"></textarea>
  </div>
</template>

<script>
  import button from './easymarkdownbutton'

  export default {
    props: ['value', 'plugins'],
    components: {
      'toolbar-button': button
    },
    data () {
      return {
        buttonsOfBase: [
          { tag: '# ', before: true, after: false, icone: 'fas fa-heading'},
          { tag: '**', before: true, after: true, icone: 'fas fa-bold'},
          { tag: '*', before: true, after: true, icone: 'fas fa-italic'},
          { tag: '* ', before: true, after: false, icone: 'fas fa-list'},
          { tag: '>', before: true, after: false, icone: 'fas fa-quote-left'},
          { tag: '```', before: true, after: true, icone: 'fas fa-code'}
        ]
      }
    },
    computed:{
      buttons () {
        if (this.plugins !== undefined && this.plugins.length > 0){
          return this.buttonsOfBase.concat(this.plugins)
        }
        return this.buttonsOfBase
      }
    },
    methods: {
      func (el) {

        let button = ''

        if (el.target.parentNode.tagName.toLowerCase().indexOf('div') >= 0 && el.target.parentNode.className.toLowerCase().indexOf('button') >= 0) {
          button = el.target.parentNode
        }
        else if (el.target.parentNode.tagName.toLowerCase().indexOf('svg') >= 0) {
          button = el.target.parentNode.parentNode
        }

        let tag = button.getAttribute('data-md')

        let after = button.getAttribute('data-after')
        let before = button.getAttribute('data-before')

        let editor = this.$el.getElementsByClassName('editor')
        editor = editor[0]

        let start = editor.selectionStart;
        let finish = editor.selectionEnd;

        let text = editor.value.substring(start, finish);

        if (before === 'true') {
           text = `${tag}${text}`
        }

        if (after === 'true') {
          text = `${text}${tag}`
        }

        editor.setRangeText(text)

        this.createInput(editor)
      },
      createInput (el) {
        let event = new Event('input', {
          'bubbles': true,
          'cancelable': true
        });

        el.dispatchEvent(event);

      },
      send (event) {
        this.$emit('input', event.target.value)
      }
    }
  }
</script>

<style scoped>
  .toolbar{
    display: flex;
    height: 1.8rem;
    background-color: #e6e6e6;
    border-left: 1px solid rgba(0, 0, 0, 0.125);
    border-right: 1px solid rgba(0, 0, 0, 0.125);
    border-top: 1px solid rgba(0, 0, 0, 0.125);
  }
  .editor{
    min-height:200px;
    display:inline-block;
    background-color: #fff;
    text-align:left;
    color: #333;
    border: 1px solid rgba(0, 0, 0, 0.125);
  }
  .container{
    width: 100%;
    margin: 0 auto;
    display: flex;
    flex-direction: column;
  }
</style>
