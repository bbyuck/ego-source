<template>
  <div class="profile_card">  
    <div class="header">
      {{ myInfo.myIngameId }}
    </div>
    <div class="under_header">
      <div class="under_header_left_high" v-bind:class="myInfo.myTier" v-if="myInfo.isHigh">
        {{ myInfo.myTier }} <br> {{myInfo.myLp + ' LP'}}
      </div>
      <div class="under_header_left" v-bind:class="myInfo.myTier" v-if="!myInfo.isHigh">
        {{ myInfo.myTier }} {{myInfo.myTierLev}}
      </div>
    </div>

      <div v-bind:class="{profile_card_tier_high_area : myInfo.isHigh, profile_card_tier_area : !myInfo.isHigh}">
        <img v-bind:src="tierImgUrlRoot + myInfo.myTier + '.png'" alt="">
      </div>
      <div class="hexa_area">
        <div class="hexa_top">
          <img v-bind:src="positionImgUrlRoot + top">
        </div>
        <div class="hexa_jg">
          <img v-bind:src="positionImgUrlRoot + jungle">
        </div>
        <div class="hexa_mid">
          <img v-bind:src="positionImgUrlRoot + mid">
        </div>
        <div class="hexa_ad">
          <img v-bind:src="positionImgUrlRoot + ad">
        </div>
        <div class="hexa_sup">
          <img v-bind:src="positionImgUrlRoot + support">
        </div>
        <div class="hexa_voice">
        </div>  
      </div>
  </div>
</template>

<script>


export default {
  data: function () {
    return {
      tierImgUrlRoot: './src/assets/images/tier/',
      positionImgUrlRoot: './src/assets/images/position/'
    }
  },
  props: ['myInfo'],
  computed: {
    top: function () {
      if(this.myInfo.myPosition[0].main) {
        return 'top_main.png';
      }
      else if(this.myInfo.myPosition[0].selected) {
        return 'top_on.png';
      }
      else {
        return 'top_off.png';
      }
    },    
    jungle: function () {
      if(this.myInfo.myPosition[1].main) {
        return 'jungle_main.png';
      }
      else if(this.myInfo.myPosition[1].selected) {
        return 'jungle_on.png';
      }
      else {
        return 'jungle_off.png';
      }
    },
    mid: function () {
      if(this.myInfo.myPosition[2].main) {
        return 'mid_main.png';
      }
      else if(this.myInfo.myPosition[2].selected) {
        return 'mid_on.png';
      }
      else {
        return 'mid_off.png';
      }
    },
    ad: function () {
      if(this.myInfo.myPosition[3].main) {
        return 'ad_main.png';
      }
      else if(this.myInfo.myPosition[3].selected) {
        return 'ad_on.png';
      }
      else {
        return 'ad_off.png';
      }
    },
    support: function () {
      if(this.myInfo.myPosition[4].main) {
        return 'support_main.png';
      }
      else if(this.myInfo.myPosition[4].selected) {
        return 'support_on.png';
      }
      else {
        return 'support_off.png';
      }
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
  display: block;
  margin-left: auto;
  margin-right: auto;
}

.header, .under_header {
  width: 90%;
  display: block;
  height: 20px;
  font-size: 20px;  
  margin-left: auto;
  margin-right: auto;
  padding-bottom: 10px;
  text-align: center;
}
.header {
  border-bottom: solid 1px #461f41;
  padding-top: 10px;
}

.under_header_left {
  float: left;
  width: 33.3%;
  height: 20px;
  font-size: 12px;
  padding-top: 3px;
  margin-top: 3px;
  border-radius: 5px;
}
.under_header_left_high {
  float: left;
  width: 33.3%;
  height: 30px;
  font-size: 12px;
  padding-top: 3px;
  margin-top: 3px;
  border-radius: 5px;
}

.Iron {
  background-color: darkgray;
}
.Bronze {
  background-color: chocolate;
}
.Silver {
  background-color: silver;
}
.Gold {
  background-color: gold;
}
.Platinum {
  background-color: aquamarine;
}
.Diamond {
  background-color: aqua;
}
.Master {
  background-color: purple;
}
.GrandMaster {
  background-color: red;
}
.Challenger {
  background-color: skyblue;
}

.profile_card_id {
  padding-bottom: 10px;
}

.header_center {
  margin-left: auto;
  margin-right: auto;
}



.profile_card_tier_area, .profile_card_tier_high_area {
  width: 30%;
  position: relative;
  display: inline-block;
  margin-left: 5%;
}
.profile_card_tier_area {
  margin-top: 10px;
}

.profile_card_tier_area > img, .profile_card_tier_high_area > img {
  width: 100%;
}

.hexa_area {
  position: relative;
  display: inline-block;
  width: 60%;
  height: 100px;
  bottom: 0px;
}

.hexa_top, .hexa_jg, .hexa_mid, .hexa_ad, .hexa_sup {
  width: 25%;
  position: absolute;
  display: block;
  top: 0;
}

.hexa_top > img, .hexa_jg > img, .hexa_mid > img, .hexa_ad > img, .hexa_sup > img {
  width: 100%;
}

.hexa_top {
  left: 20%;
}

.hexa_jg {
  left: 40%;
  top: 60px;
}

.hexa_mid {
  left: 40%;
  top: 20px;
}

.hexa_ad {
  left: 60%;
  top: 40px;
}

.hexa_sup {
  left: 60%;
}

</style>