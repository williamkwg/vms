<template>
<div id="vmarkdown">
  <textarea class="markdown"></textarea>
</div>
</template>

<script>
export default {
  name: 'vmarkdown',
  data() {
    return {
      input: '### hello',
    }
  },
  props:['markdown'],
  mounted () {
    var simplemde = new SimpleMDE({
      autofocus: true,
      autosave: {
        enabled: true,
        uniqueId: "MyUniqueID",
        delay: 1000,
      },
      renderingConfig: {
        singleLineBreaks: false,
        codeSyntaxHighlighting: true,
      },
    })
    simplemde.value(this.markdown || '')
    this.$store.commit('SET_ITEM', {
      key: 'editor',
      val: simplemde
    })
  }
}
</script>

<style lang="stylus" scoped>
#vmarkdown {
  font-size: 2.2rem;
  line-height: 25px;
}

.markdown {
  height:400px;
  max-height:500px;
}
</style>
