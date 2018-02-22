<template>
  <div @click="emit" class="button" :data-md="tag" :data-before="before" :data-after="after" >
    <i :class="icone" aria-hidden="true"></i>
  </div>
</template>
<script>
  export default {
    props: ['tag', 'before', 'after', 'icone'],
    methods:{
      emit (event) {
        this.$emit('click',event)
      }
    }
  }
</script>

<style>
  .button{
    width: 2.5rem;
    align-items: center;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    justify-content: center;
    border: 1px solid;
    padding: 0px;
    z-index: 1;
  }
  .button:hover{
    background: #c3c3c3;
  }
  .button svg{
    cursor:pointer;
  }
</style>
