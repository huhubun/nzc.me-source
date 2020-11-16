<template>
  <div class="text-center">
    <h1 class="text-md-h2 text-h4 mt-10 mb-3">关于 呼呼小笼包</h1>
    <div class="mb-6">
      <v-chip
        v-for="tag in myTags"
        class="ma-2"
        color="green darken-1"
        outlined
        :key="tag.text"
        >{{ tag.text }}</v-chip
      >
    </div>
    <div class="text-body-1">
      <p>
        呼呼小笼包
        <em>(huhubun)</em>
        是我从高中开始使用的昵称，一直沿用至今。
      </p>
      <p>
        大学就读于大连职业技术学院软件技术专业，现在从事计算机软件开发相关工作。
      </p>
    </div>

    <div>
      <site-card-group />
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    myTags: [
      {
        text: '90 后'
      },
      {
        text: '巨蟹座'
      },
      {
        text: '广西桂林人'
      },
      {
        text: '现居辽宁大连'
      },
      {
        text: '软件开发工程师'
      }
    ]
  })
}
</script>
