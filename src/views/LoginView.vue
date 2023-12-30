<script setup lang="ts">
import { FormInstance, type FormRules } from 'element-plus'
import { reactive, ref } from 'vue'
// data validation
interface LoginRule {
  role: number | null
  username: string | null
  password: string | null
}

const ruleFormRef = ref<FormInstance>()
const loginInfo = reactive<LoginRule>({
  role: null,
  username: null,
  password: null
})

const rules = reactive<FormRules<LoginRule>>({
  username: { required: true, message: 'Please input username', trigger: 'blur' },
  password: { required: true, message: 'Please input password', trigger: 'blur' }
})
// login function
const login = async (formEl: FormInstance | undefined) => {
  await formEl.validate((valid, fields) => {
    if (valid) {
      console.log('submit!')
    } else {
      console.log('error submit!', fields)
    }
  })
}
</script>
<template>
  <div class="container">
    <div class="loginBox">
      <br />
      <h2>Login as...</h2>
      <br /><br />
      <el-form
        class="form"
        :model="loginInfo"
        ref="ruleFormRef"
        :rules="rules"
        label-width="0px"
        :inline="false"
        label-position="top"
        :validate-on-rule-change="false"
      >
        <el-form-item>
          <el-radio-group v-model="loginInfo.role" fill="#8EC63F">
            <el-radio-button label="Recruiter"></el-radio-button>
            <el-radio-button label="Volunteer"></el-radio-button>
          </el-radio-group>
        </el-form-item>

        <el-form-item prop="username">
          <el-input class="input" v-model="loginInfo.username" placeholder="Username"></el-input>
        </el-form-item>
        <el-form-item prop="password">
          <el-input class="input" v-model="loginInfo.password" placeholder="Password"></el-input>
        </el-form-item>
        <el-form-item>
          <el-button class="login" @click="login(ruleFormRef)">Login</el-button>
        </el-form-item>
      </el-form>
    </div>
  </div>
</template>

<style lang="sass">
@import '@/assets/sass/variable.sass'
@import '@/assets/sass/main.sass'
// element-plus css
.el-form-item__content .el-radio-button__inner
  width: 150px
  @media (min-width: $bp-md)
    width: 200px
// normal css
h2
  color: $color-text
.container
  display: grid
  height: calc( 100vh - 60px )
  @media (min-width: $bp-md)
    background-color: #eeeeee
  .loginBox
    text-align: center
    margin: 10% auto 
    @media (min-width: $bp-md)
      // center the login box
      margin: auto
      // size
      width: 400px
      height: 70%
      max-height: 600px
      // border related
      border-radius: 10px
      border: 1px solid $color-text
      // bgcolor
      background-color: white
      // align
      padding: 30px
    .input, .login
      width: 300px
      @media (min-width: $bp-md)
        width: 400px
</style>
