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
        <CInput placeholder="Meet Address" v-model="inputs.address" />
        <CButton @click="runMeet">Go there</CButton>
      </CBox>
    </CBox>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import Heading from '~/components/Heading.vue'
export default Vue.extend({
  name: 'App',
  components: { Heading },
  data() {
    return {
      inputs: {
        address: '',
      },
    }
  },
  methods: {
    runMeet() {
      //@ts-ignore
      this.$toast({
        title: "This does not work yet...",
        description: this.inputs.address
      })
    }
  },
})
</script>
