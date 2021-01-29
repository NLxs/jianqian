<template>
  <Layout class-prefix="layout">
    <NumberPad />
    <Types />
    <Notes />
    <Tags :data-source.sync="tags" />
  </Layout>
</template>

<script lang="ts">
  import Vue from 'vue'
  import Types from '@/components/Types.vue';
  import Tags from '@/components/Tags.vue';
  import Notes from '@/components/Notes.vue';
  import NumberPad from '@/components/NumberPad.vue';
  export default Vue.extend({
    name: "Money",
    components: {
      Types,
      Tags,
      Notes,
      NumberPad
    },
    data() {
      return {
        tags: ['衣', '食', '住', '行', 'CSGO']
      }
    }
  })
</script>

<style lang="scss">
  .layout-content {
    display: flex;
    flex-direction: column-reverse;
  }
</style>
