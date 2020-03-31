<template>
  <div class="profile_card">
    <div class="profile_card_id">
      {{ myInfo.myIngameId }}
    </div>
  </div>
</template>

<script>


export default {
  data: function () {
    return {
      
    }
  },
  props: ['myInfo']
}
</script>

<style>
.profile_card {
  width: 80%;
  height: 500px;
  background-color:white;
  border-radius: 15px;
  display: inline-block;
}
</style>