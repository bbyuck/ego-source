<template>
  <div class="page_content">
    <profile-card v-bind:myInfo="myInfo"></profile-card>
  </div>
</template>

<script>
import ProfileCard from '../common/ProfileCard.vue'

export default {
  props: ['myInfo'],  
  components: {
    ProfileCard
  }
}
</script>

<style scoped>
.page_content {
  margin-top: 5%;
}
</style>