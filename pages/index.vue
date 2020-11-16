<template>
  <div>
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

    <div class="text-center">
      <h1 class="text-md-h4 text-h5 mt-10 mb-3">历程</h1>

      <div class="text-body-1">
        <p>
          小学时第一次接触到了计算机，当时还是 Windows 98 系统和大屁股的 CRT
          显示器，软磨硬泡家里终于同意让我参加计算机兴趣班，但报名当天，好像是因为前一天作业完成的不好，被班主任拒绝报名
          😂。
        </p>
        <p>
          上初中后，因为是住校生活，经常去学校图书馆，图书馆的老师向我推荐了《电脑爱好者》杂志，从此一发不可收拾。把图书馆馆藏的都看过之后，最期待的就是每周《电脑报》和每个月《电脑爱好者》上新。
        </p>
        <p>
          当时手机属于奢饰品，但是我有一台电子词典，通过它接触了 BASIC
          ，可以绘制线条，输出文本，还有大佬用它制作了游戏，我便被编程深深吸引。
        </p>
        <p>
          升入高中后开办了人生中第一个网站“呼呼小盒子”<small>（现在已倒闭）</small>。当时大家或多或少都拥有了手机，我觉得应该有一个靠谱的下载软件的地方，就用“啊估文章软件管理系统
          ASP
          版”折腾了个手机软件下载网站。当时用百度搜索“涂鸦跳跃”排名第一的一度是我这个网站。
        </p>
        <p>
          但上传别人的成果到自己网站上有悖互联网精神。当时相同功能的软件百花齐放，于是打算转型做专业软件测评网站。当然后来因为贪玩而失败，网站也被我关停了。
        </p>
        <p>
          高三下学期时开办了人生中第二个网站，基于 WordPress
          的博客，使用的是现在这个站点的域名
          nzc.me。但是因为不怎么更新，长期长草，加上 .me 域名现在无法备案，2019
          年被我关闭，博客推翻重做，便有了新的博客站点
          <a href="https://bun.plus/">bun.plus</a>。
        </p>
      </div>
    </div>

    <div>
      <h1 class="text-md-h4 text-h5 mt-10 text-center">工作</h1>

      <div class="text-center">
        <div>
          <v-row class="justify-center">
            <v-col
              v-for="card in jobCards"
              :key="card.title"
              cols="12"
              md="3"
              sm="4"
            >
              <v-card flat>
                <v-card-title class="justify-center pb-2">
                  {{ card.title }}
                </v-card-title>
                <v-card-text class="pa-0">
                  <p class="text-h5 mb-0">{{ card.text }}</p>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </div>

        <div class="text-center">
          <v-row class="justify-center">
            <v-col
              v-for="certification in certifications"
              :key="certification.title"
              cols="12"
              lg="4"
              sm="6"
            >
              <v-card outlined width="400" class="mt-5 mx-auto">
                <v-list-item class="pa-2">
                  <v-list-item-icon v-if="certification.icon" class="ma-0">
                    <v-icon :size="certificationLogoSize">
                      {{ certification.icon }}
                    </v-icon>
                  </v-list-item-icon>

                  <v-list-item-avatar
                    left
                    tile
                    :size="certificationLogoSize"
                    v-if="certification.img"
                    class="ma-0"
                  >
                    <v-img src="/images/mcsa.png" width="128"></v-img>
                  </v-list-item-avatar>

                  <v-list-item-content class="ml-3">
                    <v-list-item-title class="headline mb-1">
                      {{ certification.title }}
                    </v-list-item-title>
                    <v-list-item-subtitle>
                      {{ certification.subtitle }}
                    </v-list-item-subtitle>
                  </v-list-item-content>
                </v-list-item>
              </v-card>
            </v-col>
          </v-row>
        </div>

        <div>
          <v-row class="justify-center">
            <v-col
              v-for="(skill, index) in jobSkills"
              :key="skill.label"
              cols="12"
              sm="10"
              class="py-0"
            >
              <v-subheader class="pl-0"> {{ skill.label }} </v-subheader>
              <v-slider
                readonly
                height="10px"
                :value="skill.lv.value"
                :tick-labels="
                  index == 0 || index == jobSkills.length - 1
                    ? jobSkillLabels
                    : []
                "
                :color="skill.lv.color"
                :max="jobSkillLabels.length - 1"
                ticks="always"
              ></v-slider>
            </v-col>
          </v-row>
        </div>
      </div>
    </div>
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
  },
  computed: {},
  data() {
    const nowTime = new Date()
    const dateTimeOfFirstTimeToWork = new Date(2014, 8 - 1, 11)
    const jobSkillLabels = {
      lv1: {
        text: '了解',
        value: 0,
        color: 'grey darken-3'
      },
      lv2: {
        text: '掌握',
        value: 1,
        color: 'blue-grey'
      },
      lv3: {
        text: '熟练掌握',
        value: 2,
        color: 'blue'
      },
      lv4: {
        text: '精通',
        value: 3,
        color: 'green'
      }
    }

    return {
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
      ],
      jobCards: [
        {
          title: '工作经验',
          text: `${
            nowTime.getUTCFullYear() -
            dateTimeOfFirstTimeToWork.getUTCFullYear()
          } 年`
        },
        {
          title: '主要方向',
          text: 'ASP.NET'
        },
        {
          title: '最高职位',
          text: '开发经理'
        }
      ],

      jobSkillLabels: Object.keys(jobSkillLabels).map(key => {
        return jobSkillLabels[key].text
      }),
      certificationLogoSize: 64,
      certifications: [
        {
          title: 'RHCSA (2014)',
          subtitle: 'Red Hat Certified System Administrator',
          icon: 'mdi-redhat'
        },
        {
          title: 'MCSA (2016)',
          subtitle: 'Microsoft Certified Solutions Associate',
          img: '/images/mcsa.png'
        }
      ],

      jobSkills: [
        {
          label: 'C#',
          lv: jobSkillLabels.lv3
        },
        {
          label: 'ASP.NET MVC / Web API',
          lv: jobSkillLabels.lv3
        },
        {
          label: 'Entity Framework',
          lv: jobSkillLabels.lv3
        },
        {
          label: 'SQL Server',
          lv: jobSkillLabels.lv2
        },
        {
          label: 'Redis',
          lv: jobSkillLabels.lv2
        },
        {
          label: 'RabbitMQ',
          lv: jobSkillLabels.lv2
        },
        {
          label: 'JavaScript',
          lv: jobSkillLabels.lv3
        },
        {
          label: 'jQuery',
          lv: jobSkillLabels.lv2
        },
        {
          label: 'Vue.js',
          lv: jobSkillLabels.lv2
        },
        {
          label: 'Jenkins',
          lv: jobSkillLabels.lv2
        }
      ]
    }
  }
}
</script>
