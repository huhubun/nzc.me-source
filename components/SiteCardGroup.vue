<template>
  <v-row justify="center" align="center">
    <v-col v-for="site in sites" :key="site.href" cols="12" sm="4" lg="3">
      <v-btn
        class="white--text"
        block
        depressed
        :href="`https://${site.domain}`"
        :color="site.color"
      >
        {{ site.title }} | {{ site.domain }}
      </v-btn>
    </v-col>
  </v-row>
</template>

<script>
export default {
  data: () => ({
    sites: [
      {
        title: '博客',
        domain: 'bun.plus',
        color: 'blue-grey darken-4'
      },
      {
        title: '开发',
        domain: 'huhubun.com',
        color: 'blue darken-1'
      },
      {
        title: '摄影',
        domain: 'huhubun.lofter.com',
        color: 'light-green darken-3'
      }
    ]
  })
}
</script>
