<template>
  <div id="skill-tree-page">
    <section class="main-wrap">
      <h1 class="main-wrap__title">FRONT-END SKILL TREE</h1>

      <div class="rank-wrap">
        <div class="rank-wrap__label">CURRENT RANK</div>
        <div class="rank-wrap__name">FRONT-END NOOB</div>
      </div>

      <img src="@/static/skilltree/img-ship-noob.png" alt="" class="main-wrap__rocket-img">
      <div class="main-wrap__tips-wrap">
        <div class="tips-msg">
          Welcome aboard. Your mission is: Collect the resources and learn the skills to upgrade the ship. Good luck, captain!
        </div>
      </div>

    </section>
    <section class="steps-wrap">
      <div
        class="step-wrap"
        :class="{ 'step-wrap--disabled': stepIndex > currentStepIndex }"
        v-for="(step, stepIndex) in stepsData"
        :key="`step-${stepIndex}`">
        <div class="step-wrap__icon">
          <img :src="step.iconSrc" alt="">
        </div>
        <div class="step-wrap__courses-wrap">
          <div
            class="course-wrap"
            v-for="(course, courseIndex) in step.courses"
            :key="`course-${courseIndex}`"
            @click="stepIndex <= currentStepIndex && changeInfo(stepIndex, courseIndex)">
            <div class="course-wrap__icon">
              <i class="material-icons md-light md-36" v-text="course.icon"></i>
            </div>
            <div class="course-wrap__skills">
              <div
              class="skill"
              v-if="skillArr.length"
              v-for="(skillArr, type) in course.skills"
              :key="`course-${courseIndex}-skill-${type}`">
                <span class="skill__type">
                  <i v-if="type == 'recommend'" class="material-icons md-light md-18" v-text="`settings`"></i>
                  <i v-else-if="type == 'optional'" class="material-icons md-light md-18" v-text="`filter_tilt_shift`"></i>
                </span>
                <span class="skill__counter" v-text="`${skillArr.filter(skill => skill.isLearned).length}/${skillArr.length}`"></span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    <section class="info-wrap">
      <div class="info-wrap__header">
        <div class="info-wrap__header__icon">
          <i class="material-icons md-light md-150" v-text="currentCourse.icon"></i>
        </div>
        <div class="info-wrap__header__name" v-text="currentCourse.name"></div>
      </div>
      <div class="info-wrap__content">
        <div
          class="skills-type"
          v-for="(skillArr, type) in currentCourse.skills"
          :key="`info-${type}`"
          v-if="skillArr.length">
          <div class="skills-type__icon">
            <i v-if="type == 'recommend'" class="material-icons md-light md-36" v-text="`settings`"></i>
            <i v-else-if="type == 'optional'" class="material-icons md-light md-36" v-text="`filter_tilt_shift`"></i>
            <div class="skills-type__name" v-html="type"></div>
          </div>
          <div class="skills-options__option-btn"
            :class="{ 'skills-options__option-btn--active': skill.isLearned }"
            v-for="(skill, index) in skillArr"
            :key="`skill-${index}`"
            v-html="skill.name"
            @click="skill.isLearned = !skill.isLearned">
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
  export default {
    name: "SkillTree",
    data() {
      return {
        selectedStepIndex: 0,
        selectedCourseIndex: 0,
        stepsData: [
          {
            name: 'Basic',
            iconSrc: '/skilltree/img-planet-basics.png',
            courses: [
              {
                name: 'BASIC SKILLS',
                icon: 'category',
                skills: {
                  recommend: [
                    {
                      name: 'Learn HTML',
                      isLearned: false
                    },
                    {
                      name: 'Basics of CSS',
                      isLearned: false
                    },
                    {
                      name: 'Basics of JavaScript',
                      isLearned: false
                    },
                  ],
                  optional: [
                  ]
                }
              },
              {
                name: "BASIC TOOLS",
                icon: 'build',
                skills: {
                  recommend: [
                    {
                      name: 'Git - Version Control',
                      isLearned: false
                    },
                    {
                      name: 'Basic Terminal Usage',
                      isLearned: false
                    },
                    {
                      name: 'Text Editor',
                      isLearned: false
                    },
                    {
                      name: 'A Heart of Reserching',
                      isLearned: false
                    }
                  ],
                  optional: [
                  ]
                }
              }
            ]
          },
          {
            name: 'CSS',
            iconSrc: '/skilltree/img-planet-css.png',
            courses: [
              {
                name: 'CSS FRAMEWORK',
                icon: 'flip_to_front',
                skills: {
                  recommend: [
                    {
                      name: 'Bootstrap',
                      isLearned: false
                    },
                  ],
                  optional: [
                    {
                      name: 'UIKit',
                      isLearned: false
                    },
                    {
                      name: 'Foundation',
                      isLearned: false
                    },
                    {
                      name: 'Semantic UI',
                      isLearned: false
                    },
                  ]
                }
              },
              {
                name: 'CSS PREPROCESSORS',
                icon: 'view_quilt',
                skills: {
                  recommend: [
                    {
                      name: 'Sass',
                      isLearned: false
                    },
                    {
                      name: 'PostCSS',
                      isLearned: false
                    }
                  ],
                  optional: [
                    {
                      name: 'Less',
                      isLearned: false
                    },
                    {
                      name: 'Stylus',
                      isLearned: false
                    },
                  ]
                }
              },
              {
                name: 'CSS ARCHITECHTURE',
                icon: 'developer_board',
                skills: {
                  recommend: [
                    {
                      name: 'OOCSS',
                      isLearned: false
                    },
                  ],
                  optional: [
                    {
                      name: 'SMACSS',
                      isLearned: false
                    },
                    {
                      name: 'BEM',
                      isLearned: false
                    },
                  ]
                }
              },
              {
                name: 'CSS SKILLS',
                icon: 'devices',
                skills: {
                  recommend: [
                    {
                      name: 'Responsive Web',
                      isLearned: false
                    },
                    {
                      name: 'Flexbox',
                      isLearned: false
                    },
                  ],
                  optional: [
                  ]
                }
              },
              {
                name: 'CSS MASTERY',
                icon: 'widgets',
                skills: {
                  recommend: [
                  ],
                  optional: [
                    {
                      name: 'Grid Layout',
                      isLearned: false
                    },
                    {
                      name: 'Animation',
                      isLearned: false
                    },
                    {
                      name: 'Transform 2D, 3D',
                      isLearned: false
                    },
                  ]
                }
              }
            ]
          }
        ]
      }
    },
    computed: {
      currentStepIndex() {
        let resultIndex = 0
        const result = this.stepsData.filter(step=> {
          const stepResult = step.courses.filter(course => {
            const recommendResult = course.skills.recommend.filter(skill => {
              return !skill.isLearned
            })
            return recommendResult.length == 0
          })
          return stepResult.length == step.courses.length
        })
        resultIndex = result.length

        return resultIndex
      },
      currentCourse() {
        const { stepsData, selectedStepIndex, selectedCourseIndex } = this
        return stepsData[selectedStepIndex].courses[selectedCourseIndex]
      }
    },
    methods: {
      changeInfo(stepIndex, courseIndex) {
        this.selectedStepIndex = stepIndex
        this.selectedCourseIndex = courseIndex
      }
    }
  }
</script>

<style lang="sass" src="./style.sass" scoped>

</style>
