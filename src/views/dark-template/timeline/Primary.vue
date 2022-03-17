<template>
  <v-card
    color="grey lighten-4"
    light
  >
    <v-card-text>
      <content-section
        id="timeline"
        :title="detailed ? 'My Experiences in Software Engineering' : 'My Life'"
      >
        <template slot="actions">
          <div>
            <v-switch
              v-model="detailed"
              :label="detailed ? 'Detailed' : 'Summary'"
            />
          </div>
        </template>

        <v-timeline
          dense
        >
          <v-timeline-item
            v-for="(item, i) in orderedItems"
            :key="i"
            :icon="item.icon || ''"
            :class="{transparent: item.transparent}"
            large
          >
            <template
              v-if="item.iconImage"
              v-slot:icon
            >
              <v-avatar>
                <img
                  :src="publicPath(item.iconImage)"
                >
              </v-avatar>
            </template>
            <template v-slot:opposite />
            <v-layout>
              <v-flex
                v-if="$vuetify.breakpoint.smAndUp"
                md1
                sm2
                align-self-center
              >
                <span>{{ item.year }}</span>
              </v-flex>
              <v-flex
                md11
                sm10
                xs12
              >
                <v-card class="elevation-1">
                  <v-card-title class="pb-0">
                    <div>
                      <p v-if="$vuetify.breakpoint.xsOnly">
                        {{ item.year }}
                      </p>
                      <h3>{{ item.title }}</h3>
                    </div>
                  </v-card-title>
                  <v-card-text>
                    <v-layout wrap>
                      <v-flex
                        :md7="!!item.image"
                        :md12="!item.image"
                        xs12
                      >
                        <div class="mr-1">
                          <span
                            v-if="item.text"
                            class="pre"
                          >{{ item.text }}</span>
                          <!-- eslint-disable vue/no-v-html -->
                          <div
                            v-else-if="item.html"
                            v-html="item.html"
                          />
                          <!-- eslint-enable vue/no-v-html -->
                        </div>
                      </v-flex>
                      <v-flex
                        v-if="item.image"
                        md5
                        xs12
                      >
                        <div
                          class="mt-2"
                        >
                          <v-carousel
                            v-if="Array.isArray(item.image)"
                            :show-arrows="false"
                            :height="325"
                          >
                            <v-carousel-item
                              v-for="(citem,ci) in item.image"
                              :key="ci"
                              :src="publicPath(citem)"
                            />
                          </v-carousel>
                          <v-img
                            v-else
                            :max-height="item.imageHeight ? item.imageHeight : ''"
                            :src="publicPath(item.image)"
                          />
                        </div>
                      </v-flex>
                    </v-layout>
                  </v-card-text>
                </v-card>
              </v-flex>
            </v-layout>
          </v-timeline-item>
        </v-timeline>
      </content-section>
    </v-card-text>
  </v-card>
</template>

<script>
import ContentSection from '@/views/dark-template/content/Section'
export default {
  name      : 'Timeline',
  components: { ContentSection },
  data      : () => ({
    detailed: true,
    items   : [
      // {
      //   detailed: true,
      //   year    : 'May 2014 - Feb 2016',
      //   title   : 'Esolutions webbers - Software Engineer',
      //   html    : `
      //           <p>
      //               Worked with application debugging
      //           </p>
      //           <p>
      //               Built persistence databases with Node.js, Single Page Applications, Multi-threaded applications
      //           </p>
      //           <p>
      //               Used file normalization for sorting data, 3rd party API's
      //           </p>
      //           <p>
      //               When working in teams practiced excellent communication and focused on helping where ever and
      //           </p>
      //   `,
      //   image      : 'img/timeline/Esolutions webbers.png',
      //   imageHeight: 200,
      //   iconImage  : 'img/timeline/esolutions-webbers-icon.png',
      // },
      // {
      //   detailed: true,
      //   year    : 'Feb 2016 - Aug 2017',
      //   title   : 'Futuri Media - Full Stack Engineer',
      //   html    : `
      //           <p>
      //               Collaborated with the team members to identify business requirements to help determine the initial design of the application.
      //           </p>
      //           <p>
      //               Implemented, enhanced and maintained all three layers of the application.
      //           </p>
      //           <p>
      //               Involved in all the phases of the Software Development Life Cycle.
      //           </p>
      //           <p>
      //               Developed the presentation layer using React, Angular, SCSS, JavaScript, Bootstrap, etc.
      //           </p>
      //   `,
      //   image    : 'img/timeline/Futuri Media.png',
      //   iconImage: 'img/timeline/future-media-icon.png',
      // },
      // {
      //   detailed: true,
      //   year    : 'Aug 2017 - Dec 2018',
      //   title   : 'CloudScale Corporation - Front End Lead',
      //   html    : `
      //     <p>
      //       Worked in an Agile software development team in the development of proprietary software, involving managing a backlog of user stories in Azure DevOps
      //     </p>
      //     <p>
      //       Communicated with a team to overcome coding obstacles, and working on front end features and bug fixes.
      //     </p>
      //     <p>
      //       Built a messaging feature for users, allowing admins quick access to employee's work history, and implementing a calendar interface for scheduling.
      //     </p>
      //     <p>
      //       Built a full-stack web application with a user database, using Ruby on Rails, React, etc.
      //     </p>
      //   `,
      //   image    : 'img/timeline/CloudScale Corporation.png',
      //   iconImage: 'img/timeline/cloudScale-corporation-icon.png',
      // },
      {
        detailed: true,
        year    : 'Oct 2018 - Dec 2019',
        title   : 'PicnicHealth - Full-stack Developer',
        html    : `
                <p>
                    Worked on React/Node/Express-based application, validating query string with regex.
                </p>
                <p>
                    Communicated with clients and presented any changes I made.
                </p>
                <p>
                    Refactored large methods of multiple reusable and maintainable methods.
                </p>
                `,
        image    : 'img/timeline/PicnicHealth.png',
        iconImage: 'img/timeline/picnic-health-icon.png',
      },
      {
        detailed: true,
        year    : 'Jan 2020 - Jan 2021',
        title   : 'Outdoorsy - Senior Frontend Developer',
        html    : `
                    <p>
                        Converted legacy app was written by Ember.js to Next.js with Typescript.
                    </p>
                    <p>
                        Focused on mobile-first development and used CSS-in-JS library, emotion, with Next.js.
                    </p>
                    <p>
                        Collaborated with the back-end team using swagger UI to get API definitions.
                    </p>
                    <p>
                        Wrote unit tests and integration tests with react-testing-library.
                   </p>`,
        image    : 'img/timeline/Outdoorsy.png',
        iconImage: 'img/timeline/outdoorsy-icon.png',
      },
      {
        detailed: true,
        year    : 'Mar 2021 - Nov 2021',
        title   : 'Splash Financial - Senior Software Engineer',
        /* eslint-disable no-useless-escape */
        html    : `
                <p>
                    Primarily tasked with the creation of a serving application built using React and Material-UI.
                </p>
                <p>
                    Provided ongoing bug fixes and enhancements to our existing internal applications.
                </p>
                <p>
                    Utilized Jest and Enzyme for front-end unit testing.
                </p>
                <p>
                    Contributed to the evangelization of UI/UX best practices and code standards by encouraging a team
                </p>
                `,
        image    : 'img/timeline/Splash Financial.png',
        iconImage: 'img/timeline/splash-financial-icon.png',
      },
      // {
      //   year : 'So far ...',
      //   title: 'Written 340+ Unique Articles!',
      //   html : `I'm the guy who loves teaching! So far, I've written 340+ unique articles which most of them are computer-related. You can access them here:
      //               <ul><li><a target="_blank" href="https://bytegate.ir/author/amirrezanasiri/">My posts on Bytegate.ir</a> (260+ Computer-related)</li><li><a target="_blank" href="http://bobet.ir/author/amirrezanasiri/">My posts on Bobet.ir</a> (80+ translations)</li></ul>`,
      //   icon: 'mdi-fountain-pen-tip',
      // },
    ],
  }),
  computed: {
    orderedItems () {
      const items = [...this.items].reverse()
      if (this.detailed)
        return items
      return items.filter((item) => {
        return !item.detailed
      })
    },
  },
}
</script>

<style scoped>
.title {
  border-bottom: 2px #bfbfbf solid;
  line-height: 1.5 !important;
}
.pre {
  white-space: pre;
}
.transparent{
  opacity: 0.6;
}
</style>
