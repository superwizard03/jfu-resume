<template>
  <v-card
    color="grey lighten-4"
    light
  >
    <v-card-text>
      <content-section
        title="Who am I?"
      >
        As a senior software engineer dedicated to Javascript development in last 10 years, I specialize in React, Vue.js, and Angular for front-end development and Solidity, Node.js, Django, and Ruby on Rails for back-end development.<br>
        I can do ANYTHING you need to build your app from the ground-up and get it on the market which means I can turn your conceptual ideal to real working software.<br>
        My rich experiences started from C and C++(object-oriented language) When I was 13 years old, I started programming simple algorithms with C and since 15, I participated in more complex algorithm development using C++, ranging from small to large game engines and delivered brilliant results of all projects.<br>
        During my school days, I was able to master C/C++ programming and it makes me learn the other popular web stacks (React, Vue.js, Angular) more easily.  I started web development after graduating from school.<br>
        With professional skills, I had been working on various projects as a full-stack developer in a variety of industries.<br>
        Also, I’m an experienced Blockchain Software Engineer & Blockchain Consultant specializing in creating secure and optimized smart contracts using Solidity for EVM (Ethereum Virtual Machine) compatible blockchains.<br><br>
        I’m able to create smart contracts and connect them with web browsers to provide clean and easy-to-use web interfaces using tools like React, Redux, Web3.js, Ethers.js, TypeScript, Next.js, etc.
      </content-section>
      <content-section
        v-if="prouds"
        title="What am I proud of?"
      >
        <v-layout
          v-for="(proud, i) in prouds"
          :key="i"
        >
          <v-flex
            md1
            xs3
          >
            <v-icon right>
              {{ proud.icon }}
            </v-icon>
          </v-flex>
          <v-flex
            md11
            xs9
          >
            <p>
              <strong>{{ proud.text }}</strong><br>
              <small>{{ proud.source }}</small>
            </p>
          </v-flex>
        </v-layout>
      </content-section>
      <content-section
        v-if="educations"
        title="Education"
      >
        <v-layout
          v-for="(education, i) in educations"
          :key="i"
        >
          <v-flex md4>
            {{ education.from }} - {{ education.to }}
          </v-flex>
          <v-flex md8>
            <strong v-if="education.title">{{ education.title }}</strong>
            <div v-if="education.location">
              <i>{{ education.location }}</i>
            </div>
            <div v-if="education.description">
              {{ education.description }}
            </div>
          </v-flex>
        </v-layout>
      </content-section>
      <content-section
        v-if="skills"
        id="to-timeline"
        title="Skills"
      >
        <template slot="actions">
          (% are relative not absolute)
        </template>
        <v-layout wrap>
          <template
            v-for="(skill, i) in skills"
          >
            <v-flex
              v-if="skill.divider"
              :key="i"
              md12
              xs12
              mb-4
            />
            <v-flex
              v-else
              :key="i"
              md6
              xs12
            >
              <div
                class="mr-2 ml-2"
              >
                <div class="align-center">
                  <v-icon
                    small
                  >
                    {{ skill.icon }}
                  </v-icon>
                  {{ skill.title }}
                </div>
                <v-progress-linear
                  class="progress"
                  color="secondary"
                  height="3"
                  :value="skill.value"
                />
              </div>
            </v-flex>
          </template>
        </v-layout>
      </content-section>
    </v-card-text>
  </v-card>
</template>

<script>
import ContentSection from '@/views/dark-template/content/Section'
export default {
  name      : 'MainContent',
  components: { ContentSection },
  data      : () => ({
    prouds: [
      {
        icon  : 'mdi-star',
        text  : '✔ Hard working professional, ready to take on new challenges',
        source: '',
      },
      {
        icon  : 'mdi-hand-peace',
        text  : '✔ Professional in all dealings',
        source: '',
      },
      {
        icon  : 'mdi-timer-sand',
        text  : '✔ Ability to deliver on time under tight deadlines',
        source: '',
      },
      {
        icon  : 'mdi-wechat',
        text  : '✔ Great communication skills',
        source: '',
      },
      {
        icon  : 'mdi-face-agent',
        text  : '✔ Passionate and self-driven',
        source: '',
      },
    ],
    educations: [
      {
        from       : '2014',
        to         : '2018',
        title      : 'Bachelor\'s degree, Computer Science',
        location   : 'DongBei University',
        description: 'During my school days, I was able to master C/C++ programming and it makes me learn the other popular web stacks (React, Vue.js, Angular) more easily.  I started web development after graduating from school.',
      },
    ],
    skills: [
      {
        title: 'PHP',
        icon : 'mdi-language-php',
        value: 95,
      },
      {
        title: 'JavaScript',
        icon : 'mdi-language-javascript',
        value: 95,
      },
      {
        title: 'Laravel',
        icon : 'mdi-laravel',
        value: 90,
      },
      {
        title: 'React.js/Next.js',
        icon : 'mdi-react',
        value: 99,
      },
      { divider: true },
      {
        title: 'Node.js/Express',
        icon : 'mdi-nodejs',
        value: 99,
      },
      {
        title: 'Vue.js/Nuxt.js',
        icon : 'mdi-vuejs',
        value: 90,
      },
      {
        title: 'Python/Django',
        icon : 'mdi-shield-lock',
        value: 85,
      },
      {
        title: 'Angular.js/Angular(2 ~ 12)',
        icon : 'mdi-test-tube',
        value: 86,
      },
      {
        title: 'Git/Github/Bitbucket',
        icon : 'mdi-truck-fast',
        value: 98,
      },
      {
        title: 'Wordpress Design',
        icon : 'mdi-git',
        value: 80,
      },
      { divider: true },
      {
        title: 'Blockchain Development/Smart Contract',
        icon : 'mdi-chip',
        value: 50,
      },
      {
        title: 'API Integration/Swagger/Strapi',
        icon : 'mdi-language-cpp',
        value: 95,
      },
      { divider: true },
      {
        title: 'C++/C#/Java/Spring',
        icon : 'mdi-account-group',
        value: 60,
      },
      {
        title: 'DevOps',
        icon : 'mdi-text',
        value: 70,
      },
    ],
  }),
}
</script>

<style scoped>
.title {
  border-bottom: 2px #bfbfbf solid;
  line-height: 1.5 !important;
}
.progress {
  margin-top: 0.1rem;
}
</style>
