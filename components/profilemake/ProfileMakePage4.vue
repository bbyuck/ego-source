<template>
  <div class="page_content">
    <div class="selected_playstyle_area">
      <div class="gray_header1">
        <p class="header_text">
          선택한 ego태그
        </p>
      </div>
    </div>
    <div class="playstyle_area">
      <div class="gray_header2">
        <p class="header_text">
          ego태그 목록
        </p>
      </div>
      <div class="position_category">
        <div class="position_btn_container">
          <div class="position_btn" v-on:click="positionFilter('top')">
            <img v-show="topBtnOn" v-bind:src="btnUrl + 'top_on.png'" alt="">
            <img v-show="!topBtnOn" v-bind:src="btnUrl + 'top_off.png'" alt="">
          </div>
        </div>
        <div class="position_btn_container">
          <div class="position_btn" v-on:click="positionFilter('jg')">
            <img v-show="jgBtnOn" v-bind:src="btnUrl + 'jg_on.png'" alt="">
            <img v-show="!jgBtnOn" v-bind:src="btnUrl + 'jg_off.png'" alt="">
          </div>
        </div>
        <div class="position_btn_container">
          <div class="position_btn" v-on:click="positionFilter('mid')">
            <img v-show="midBtnOn" v-bind:src="btnUrl + 'mid_on.png'" alt="">
            <img v-show="!midBtnOn" v-bind:src="btnUrl + 'mid_off.png'" alt="">
          </div>
        </div>
        <div class="position_btn_container">
          <div class="position_btn" v-on:click="positionFilter('ad')">
            <img v-show="adBtnOn" v-bind:src="btnUrl + 'ad_on.png'" alt="">
            <img v-show="!adBtnOn" v-bind:src="btnUrl + 'ad_off.png'" alt="">
          </div>
        </div>
        <div class="position_btn_container">
          <div class="position_btn" v-on:click="positionFilter('sup')">
            <img v-show="supBtnOn" v-bind:src="btnUrl + 'sup_on.png'" alt="">
            <img v-show="!supBtnOn" v-bind:src="btnUrl + 'sup_off.png'" alt="">
          </div>
        </div>
      </div>

      <div class="playstyle_list">
        {{ filter }} ego태그 정보
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      btnUrl: './src/assets/images/profile_make_btn/',
      topBtnOn: true,
      jgBtnOn: false,
      midBtnOn: false,
      adBtnOn: false,
      supBtnOn: false,
      filter: 'Top'
    }
  },
  methods: {
    positionFilter: function (payload) {
      
      switch(payload) {
      case 'top':
        this.topBtnOn = true;
        this.jgBtnOn = false;
        this.midBtnOn = false;
        this.adBtnOn = false;
        this.supBtnOn = false;
        this.filter = "Top";
        break;
      case 'jg':
        this.topBtnOn = false;
        this.jgBtnOn = true;
        this.midBtnOn = false;
        this.adBtnOn = false;
        this.supBtnOn = false;
        this.filter = "Jungle";
        break;
      case 'mid':
        this.topBtnOn = false;
        this.jgBtnOn = false;
        this.midBtnOn = true;
        this.adBtnOn = false;
        this.supBtnOn = false;
        this.filter = "Mid";
        break;
      case 'ad':
        this.topBtnOn = false;
        this.jgBtnOn = false;
        this.midBtnOn = false;
        this.adBtnOn = true;
        this.supBtnOn = false;
        this.filter = "AD Carry";
        break;
      case 'sup':
        this.topBtnOn = false;
        this.jgBtnOn = false;
        this.midBtnOn = false;
        this.adBtnOn = false;
        this.supBtnOn = true;
        this.filter = "Support";
        break;
      default:
        break;
      }
    }
  }
}
</script>

<style>
.selected_playstyle_area {
  height: 150px;
}

.position_category {
  text-align: center;
  margin-top: 10px;
}
.position_btn_container {
  width: 18%;
  display: inline-block;
}

.position_btn img {
  width: 100%;
}

</style>