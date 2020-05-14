<template>
  <div class="page_content">
    <div class="selected_playstyle_area">
      <div class="gray_header1">
        <p class="header_text">
          선택한 플레이스타일
        </p>
      </div>
    </div>
    <div class="playstyle_area">
      <div class="gray_header2">
        <p class="header_text">
          플레이스타일 목록
        </p>
      </div>
      <div class="position_category">
        <div class="position_btn_container">
          <div class="position_btn" v-on:click="positionFilter('top')">
            <img v-bind:src="btnUrl + topBtn" alt="">
          </div>
        </div>
        <div class="position_btn_container">
          <div class="position_btn" v-on:click="positionFilter('jg')">
            <img v-bind:src="btnUrl + jgBtn" alt="">
          </div>
        </div>
        <div class="position_btn_container">
          <div class="position_btn" v-on:click="positionFilter('mid')">
            <img v-bind:src="btnUrl + midBtn" alt="">
          </div>
        </div>
        <div class="position_btn_container">
          <div class="position_btn" v-on:click="positionFilter('ad')">
            <img v-bind:src="btnUrl + adBtn" alt="">
          </div>
        </div>
        <div class="position_btn_container">
          <div class="position_btn" v-on:click="positionFilter('sup')">
            <img v-bind:src="btnUrl + supBtn" alt="">
          </div>
        </div>
      </div>

      <div class="playstyle_list">
        {{ filter }} 특징 정보
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      btnUrl: './src/assets/images/profile_make_btn/',
      topBtn: 'top_off.png',
      jgBtn: 'jg_off.png',
      midBtn: 'mid_off.png',
      adBtn: 'ad_off.png',
      supBtn: 'sup_off.png',
      filter: ''
    }
  },
  methods: {
    positionFilter: function (payload) {
      switch(this.filter) {
      case 'Top':
        if(payload !== 'top') {
          this.topBtn = 'top_off.png';
        }
        break;
      case 'Jungle':
        if(payload !== 'jg') {
          this.jgBtn = 'jg_off.png';
        }
        break;
      case 'Mid':
        if(payload !== 'mid') {
          this.midBtn = 'mid_off.png';
        }
        break;
      case 'AD Carry':
        if(payload !== 'ad') {
          this.adBtn = 'ad_off.png';
        }
        break;
      case 'Support':
        if(payload !== 'sup') {
          this.supBtn = 'sup_off.png';
        }
        break;
      default:
        break;
      }

      switch(payload) {
      case 'top':
        this.filter = 'Top';
        this.topBtn = 'top_on.png';
        break;
      case 'jg':
        this.filter = 'Jungle';
        this.jgBtn = 'jg_on.png';
        break;
      case 'mid':
        this.filter = 'Mid';
        this.midBtn = 'mid_main.png';
        break;
      case 'ad':
        this.filter = 'AD Carry';
        this.adBtn = 'ad_on.png';
        break;
      case 'sup':
        this.filter = 'Support';
        this.supBtn = 'sup_on.png';
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