<template>
  <div class="container">
    <CBox
      d="flex"
      w="100vw"
      h="100vh"
      flex-dir="column"
      justify-content="center"
    >
      <Heading />
      <CBox :w="['95%', '80%', '50%', '30%']" mt="10" mx="auto">
        <CInput placeholder="Login Address" v-model="inputs.email" />
        <CInput
          placeholder="Password"
          type="password"
          v-model="inputs.password"
        />

        <CInput placeholder="Meet Code" v-model="inputs.address" />
        <CInput
          placeholder="Custom Meet Load Wait Time"
          v-model="inputs.customWait"
        />
        <CInput placeholder="Meet Duration" v-model="inputs.meetDuration" />
        <br />
        <CButton @click="runMeet">Go there</CButton>
      </CBox>
    </CBox>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import fs from 'fs'
import { execFile } from 'child_process'
import Heading from '~/components/Heading.vue'

export default Vue.extend({
  name: 'App',
  components: { Heading },
  data() {
    return {
      inputs: {
        address: '',
        email: '',
        password: '',
        customWait: undefined,
        meetDuration: undefined,
      },
    }
  },
  methods: {
    runMeet() {
      fs.writeFileSync(
        '~/creds.json',
        `{\n    "email": "${this.inputs.email}",\n    "password": "${this.inputs.password}"\n}`
      )
      execFile('../index.ts', [
        `https://meet.google.com/${this.inputs.address}`,
        String(this.inputs.meetDuration),
        String(this.inputs.customWait),
      ])

      //@ts-ignore
      this.$toast({
        title: 'Launching',
        description: `meet.google.com/${this.inputs.address}`,
      })
    },
  },
})
</script>
