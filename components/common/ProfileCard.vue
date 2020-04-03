<template>
  <div class="profile_card">
    <div class="header">
      <div class="tier_text header_left">
        {{ myInfo.myTier }} {{ myInfo.myIsHigh ? myInfo.myLp + ' LP' : myInfo.myTierLev }}
      </div>
      <div class="profile_card_id header_center">
        {{ myInfo.myIngameId }}
      </div>
    </div>
        <div class="content">
      <div class="profile_card_tier">
        <img v-bind:src="tierImgUrlRoot + myInfo.myTier + '.png'" alt="">
      </div>
    </div>
  </div>
</template>

<script>


export default {
  data: function () {
    return {
      
    }
  },
  props: ['myInfo'],
  computed: {
    tierImgUrlRoot: function () {
      return this.$store.state.tierImgRoot;
    }
  }
}
</script>

<style>
.profile_card {
  width: 80%;
  height: 500px;
  background-color:white;
  border-radius: 15px;
  display: inline-block;
  text-align: center;
}

.header {
  width: 80%;
  display: inline-block;
  border-bottom: solid 1px #461f41;
  padding-top: 10px;
  margin-left: auto;
  margin-right: auto;
  text-align: center;
}

.header_left, .header_right, .header_center {
  float: left;
}

.header_left, .header_right {
  width: 25%;
}

.profile_card_id {
  padding-bottom: 10px;
}

.header_center {
  width: 50%;
}

.tier_text {
  background-color: skyblue;
  font-size: 10px;
  border-radius: 5px;
}

.content {
  width: 100%;
  float: left;
}

.profile_card_tier {
  width: 35%;
  margin-left: 10%;
  margin-top: 20px;
}

.profile_card_tier > img {
  width: 100%;
}
</style>