<template>
  <div @click="emit" class="btn" :data-md="tag" :data-before="before" :data-after="after" >
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
