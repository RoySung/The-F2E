<template>
  <div id="validation-page">
    <hr/>
    <el-steps :active="activeStep" finish-status="success">
      <el-step v-for="index in stepsConfig.length" :key="index">
        <div slot="icon" class="circle-icon" />
      </el-step>
    </el-steps>
    <div class="steps-content">
      <div class="title-wrap">
        <h1 class="title-wrap__title" v-html="stepsConfig[activeStep].title" />
        <h3 class="title-wrap__desc" v-html="stepsConfig[activeStep].desc" />
      </div>

      <div v-if="activeStep == 0" class="step-wrap">
        <span class="step-wrap__line">
          <div class="input-wrap">
            <label>Account</label>
            <el-input
              v-model="stepsConfig[0].fields.account"
              placeholder="Your Name">
            </el-input>
          </div>
        </span>
        <span class="step-wrap__line">
          <div class="input-wrap">
            <label>Password</label>
            <el-input
              type="password"
              v-model="stepsConfig[0].fields.password"
              placeholder="Your Name">
            </el-input>
          </div>
        </span>
        <span class="step-wrap__line">
          <div class="input-wrap">
            <label>Comfirm Password</label>
            <el-input
              type="password"
              v-model="stepsConfig[0].fields.comfirmPassword"
              placeholder="Your Name">
            </el-input>
          </div>
        </span>
      </div>
      <div v-if="activeStep == 1" class="step-wrap">
        <span class="step-wrap__line">
          <div class="input-wrap">
            <label>Name (optional)</label>
            <el-input
              v-model="stepsConfig[1].fields.name"
              placeholder="Your Name">
            </el-input>
          </div>
          <div class="input-wrap">
            <label for="name">Phone*</label>
            <el-input
              type="tel"
              :required="stepsConfig[1].fields.phone"
              pattern="^[09]{2}[0-9]{8}$"
              v-model="stepsConfig[1].fields.phone"
              placeholder="0912 345 678">
            </el-input>
          </div>
        </span>
        <span class="step-wrap__line">
          <div class="input-wrap">
            <label>Birth Date (optional)</label>
            <el-date-picker
              type="date"
              v-model="stepsConfig[1].fields.birth"
              placeholder="Pick Date"/>
          </div>
        </span>
        <span class="step-wrap__line">
          <div class="input-wrap">
            <label>Address*</label>
            <p class="input-wrap__line">
              <el-input
                :required="stepsConfig[1].fields.city"
                v-model="stepsConfig[1].fields.city"
                placeholder="City">
              </el-input>
              <el-input
                :required="stepsConfig[1].fields.dist"
                v-model="stepsConfig[1].fields.dist"
                placeholder="Dist">
              </el-input>
            </p>
            <el-input v-model="stepsConfig[1].fields.addressDetail" placeholder="Address Detail"></el-input>
          </div>
        </span>
      </div>

    </div>
    <el-button :disabled="!isCompleteStep" class="next-step-btn" type="primary" @click="nextStep" v-html="nextButtonText"></el-button>
  </div>
</template>

<script>
  import { Steps, Step, Button, Input, DatePicker } from 'element-ui'
  import 'element-ui/lib/theme-chalk/index.css'

  export default {
    name: "Validation",
    data() {
      return {
        activeStep: 0,
        stepsConfig: [
          {
            title: 'Create Account',
            desc: 'Glad to see you here!',
            fields: {
              account: null,
              password: null,
              comfirmPassword: null
            }
          },
          {
            title: 'General Infomation',
            desc: 'Tell us who you are!',
            fields: {
              name: null,
              phone: null,
              birth: null,
              city: null,
              dist: null,
              addressDetail: null
            }
          },
          {
            title: 'Update Profile Picture',
            desc: 'We wanna know you more!'
          },
          {
            title: 'Payment Method',
            desc: 'Add your credit card infomation! '
          },
        ]
      }
    },
    computed: {
      isLastStep() {
        return this.activeStep == this.stepsConfig.length - 1
      },
      nextButtonText() {
        return this.isLastStep ? 'Done' : 'Next'
      },
      currentStepConfig() {
        return this.stepsConfig[this.activeStep]
      },
      currentFields() {
        return this.currentStepConfig.fields
      },
      isCompleteStep() {
        return !Object.keys(this.currentFields).map(key => !!this.currentFields[key]).includes(false)
      },
    },
    methods: {
      nextStep() {
        if (!this.isLastStep) {
          let step = this.activeStep + 1
          this.activeStep = step
        }
      }
    },
    components: {
      ElSteps: Steps,
      ElStep: Step,
      ElButton: Button,
      ElInput: Input,
      ElDatePicker: DatePicker
    }
  }
</script>

<style lang="sass" src="./Validation/index.sass" scoped>

</style>
