<template>
  <div class="container">
    <CBox
      d="flex"
      w="100vw"
      h="100vh"
      flex-dir="column"
      justify-content="center"
    >
      <CHeading text-align="center" mb="4"> ⚡️ AutoMeet. </CHeading>
      <CFlex justify="center" direction="column" align="center">
        <CBox mb="3">
          <CButton left-icon="info" variant-color="blue"> Let's go </CButton>
        </CBox>
      </CFlex>
    </CBox>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  name: 'App',
})
</script>
