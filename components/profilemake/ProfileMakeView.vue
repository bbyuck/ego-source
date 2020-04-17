<template>
  <div class="profile_make">
    <div class="profile_make_page">
    <v-ons-page>
      <v-ons-carousel fullscreen swipeable auto-scroll auto-scroll-ratio="0.1"
        :index.sync="pageIndex"
      >
        <v-ons-carousel-item class="profile_make_page">
          <div class="profile_make_header">
            소환사 정보
          </div>
          <div class="profile_make_content_long">
            <profile-make-page1 v-on:idOk="idSave"
              v-on:idEmpty="resetId"
              v-on:tierSelect="tierSelectInView"
              v-on:setLp="setLpInView"
              v-on:setTierLev="setTierLevInView"
              v-on:resetLp="preMyInfo.myLp = 0"
              v-on:resetTierLev="preMyInfo.myTierLev = 1"
              ></profile-make-page1>
          </div>
        </v-ons-carousel-item>
        <v-ons-carousel-item class="profile_make_page">
          <div class="profile_make_header">
            소환사 정보
          </div>
          <div class="profile_make_content_long">

          </div>
        </v-ons-carousel-item>
        <v-ons-carousel-item class="profile_make_page">
          <div class="profile_make_header">
            챔피언 선택
          </div>
          <div class="input_area">
            <div class="input_box">
              <input type="text" class="background_input" placeholder="챔피언을 검색해주세요." v-on:input="championSearchInput" ref="championSearch">
              <div class="search_btn" v-on:click="championSearchBarBtn">
                <i class="fas fa-search" v-show="championInput === ''"></i>
                <i class="fas fa-times" v-show="championInput !== ''"></i>
              </div>
            </div>
          </div>
          <div class="profile_make_content">
            <profile-make-page3 
              v-bind:searchInput="championInput"
              v-on:championUpdate="championUpdateInView"
              ></profile-make-page3>
          </div>
        </v-ons-carousel-item>
        <v-ons-carousel-item class="profile_make_page">
          <div class="profile_make_header">
            특징 선택
          </div>

          <div class="input_area">
            <div class="input_box">
              <input type="text" class="background_input" placeholder="플레이스타일을 검색해주세요." v-on:input="playstyleSearchInput" ref="playstyleSearch">
              <div class="search_btn" v-on:click="playstyleSearchBarBtn">
                <i class="fas fa-search" v-show="playstyleInput === ''"></i>
                <i class="fas fa-times" v-show="playstyleInput !== ''"></i>
              </div>
            </div>
          </div>

          <div class="profile_make_content">

          </div>
        </v-ons-carousel-item>
        <v-ons-carousel-item class="profile_make_page">
          <div class="profile_make_header">
            프로필 카드
          </div>
          <div class="profile_card_area">
            <profile-make-page5 v-bind:myInfo="preMyInfo" 
              v-on:goToIngameIdInView="pageIndex = 0" 
              v-on:goToChampionInView="pageIndex = 2"
              ></profile-make-page5>
          </div>
        </v-ons-carousel-item>
      </v-ons-carousel>

      <div v-bind:class="{ white_dot : pageIndex === 4, progress_dot : pageIndex !== 4 }">
        <span :index="dotIndex - 1" v-for="dotIndex in 5" :key="dotIndex" style="cursor: pointer" @click="pageIndex = dotIndex - 1">
          {{ pageIndex === dotIndex - 1 ? '\u25CF' : '\u25CB' }}
        </span>
      </div>    
    </v-ons-page>    
    </div>
  </div>
</template>

<script>
import ProfileMakePage1 from './ProfileMakePage1.vue';

import ProfileMakePage3 from './ProfileMakePage3.vue';

import ProfileMakePage5 from './ProfileMakePage5.vue';

export default {
  data: function () {
    return {
      pageIndex: 0,
      championInput: '',
      completed: [false, false, false, false, false],
      playstyleInput: '',
      preMyInfo: {
        myIngameId: '',
        myTier: 'Platinum',
        isHigh: false,
        myLp : 0,
        myTierLev: 1,
        myPosition: [
          { position: "Top", selected: false ,main: false },
          { position: "Jungle", selected: false, main: false },
          { position: "Mid", selected: false, main: false },
          { position: "AD Carry", selected: false, main: false },
          { position: "Support", selected: false, main: false }
        ],
        myMainPositionIdx: -1,
        isVoiceOn: true,
        myChampions: [],
        myPlayStyles: []
      }
    }
  },
  methods:{
    idSave: function (payload) {
      this.preMyInfo.myIngameId = payload;
      this.completed[0] = true;
    },
    resetId: function (){
      this.preMyInfo.myIngameId = '';
      this.completed[0] = false;
    },
    tierSelectInView: function (payload) {
      this.preMyInfo.myTier = payload;
      if (payload === 'Challenger' || payload === 'GrandMaster' || payload === 'Master') {
        this.preMyInfo.isHigh = true;
      } 
      else {
        this.preMyInfo.isHigh = false;
      }
    },
    setLpInView: function (payload) {
      this.preMyInfo.myLp = payload;
    },
    setTierLevInView: function (payload) {
      this.preMyInfo.myTierLev = payload;
    },
    championSearchInput: function(e) {
      this.championInput = e.target.value;
    },
    championSearchBarBtn: function () {
      if(this.championInput === '') {
        this.$refs.championSearch.focus();
      }
      else {
        this.championInput = '';
        this.$refs.championSearch.value = '';
      }
    },
    championUpdateInView: function (payload) {      
      this.preMyInfo.myChampions = payload;
      if(this.preMyInfo.myChampions.length === 3) {
        this.completed[2] = true;
      }
    },
    playstyleSearchInput: function (e) {
      this.playstyleInput = e.target.value;
    },
    playstyleSearchBarBtn: function () {
      if(this.playstyleInput === '') {
        this.$refs.playstyleSearch.focus();
      }
      else {
        this.playstyleInput = '';
        this.$refs.playstyleSearch.value = '';
      }
    }
  },
  components: {
    ProfileMakePage1,
    ProfileMakePage3,
    ProfileMakePage5
  }
}
</script>

<style>
.profile_make_page {
  background-color: #461f41;
  height: 100%;
}

.progress_dot {
  text-align: center;
  font-size: 30px;
  color: #461f41;
  position: absolute;
  bottom: 20px;
  left: 0;
  right: 0;
}

.white_dot {
  color: white;
  text-align: center;
  font-size: 30px;
  position: absolute;
  bottom: 20px;
  left: 0;
  right: 0;
}

.profile_make_header {
  text-align: center;
  background-color: #461f41;
  color: #fff;
  font-size: 30px;
  margin-top: 5%;
}

.profile_make_content_long {
  background-color: #fff;
  height: 90%;
  width: 100%;
  position: absolute;
  bottom:0;
  border-radius: 20px 20px 0 0;
}

.profile_make_content {
  background-color: #fff;
  height: 78%;
  width: 100%;
  position: absolute;
  bottom: 0;
  border-radius: 20px 20px 0 0;
}

.tab_title {
  font-size: 20px;
  margin: 5px;
  color: #461f41;
}

.tab_desc {
  font-size: 13px;
  margin: 5px;
  color: gray;
}

.page_content {
  height: 100%;
}

.input_area {
  text-align: center;
}

.input_box {
  width: 80%;
  height: 40px;
  border-radius: 10px;
  text-align: center;
  box-shadow: 2px 2px 2px 2px black;
  border: solid #461f41 1px;
  margin-top: 10px;
  margin-top: 10px;
  margin-left: auto;
  margin-right: auto;
  background-color: #fff;
  padding-top: 10px;
}

.search_btn {
  display: inline-block;
  width: 15%;
  height: 30px;
}

.search_btn > i {
  color: #461f41;
}

.background_input {
  background-color: inherit;
  font-size: 20px;
  height: 25px;
  width: 70%;
  text-align: center;
  border: none;
}

.profile_card_area {
  margin-left: auto;
  margin-right: auto;
}

</style>