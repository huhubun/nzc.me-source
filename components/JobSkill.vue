<template>
  <div>
    <h1 class="text-md-h4 text-h5 text-center">工作</h1>

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
                  tile
                  :size="certificationLogoSize"
                  v-if="certification.img"
                  class="ma-0"
                >
                  <v-img src="/images/mcsa.png"></v-img>
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
</template>

<script>
export default {
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

<style>
</style>