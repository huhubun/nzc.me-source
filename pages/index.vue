<template>
  <div>
    <top-about />
    <v-divider class="my-10" />

    <my-experience />
    <v-divider class="my-10" />

    <job-skill />

    <div style="my-10">&nbsp;</div>
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: '首页',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: '这里是呼呼小笼包的介绍，可以进一步了解他。'
        },
        {
          hid: 'keywords',
          name: 'keywords',
          content: '关于呼呼小笼包,nzc.me,呼呼小笼包,huhubun,'
        }
      ]
    }
  }
}
</script>
