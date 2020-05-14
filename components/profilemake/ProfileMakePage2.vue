<template>
  <div class="page_content">
    <div class="tab_title">
      보이스 채팅
    </div>
    <div class="tab_desc">
      게임중 회원님의 보이스 채팅 여부를 선택해주세요.
    </div>

    <div class="voice_area">
      <div class="voice_btn_container">
        <div class="voice_btn" v-on:click="micOn">
          <img v-bind:src="btnUrl + micBtnLeft">
        </div>
      </div>
      <div class="voice_btn_container">
        <div class="voice_btn" v-on:click="micOff">
          <img v-bind:src="btnUrl + micBtnRight">
        </div>
      </div>
    </div>

    <div class="tab_title">
      포지션 선택
    </div>
    <div class="tab_desc">
      회원님의 포지션을 한 개 이상 선택해주세요.
    </div>
    <div class="position_area">
      <div class="position_btn_container">
        <div class="position_btn" v-on:click="topToggle">
          <img v-bind:src="btnUrl + topBtn">
        </div>
      </div>
      <div class="position_btn_container">
        <div class="position_btn" v-on:click="jgToggle">
          <img v-bind:src="btnUrl + jgBtn">
        </div>
      </div>
      <div class="position_btn_container">
        <div class="position_btn" v-on:click="midToggle">
          <img v-bind:src="btnUrl + midBtn">
        </div>
      </div>
      <div class="position_btn_container">
        <div class="position_btn" v-on:click="adToggle">
          <img v-bind:src="btnUrl + adBtn">
        </div>
      </div>
      <div class="position_btn_container">
        <div class="position_btn" v-on:click="supToggle">
          <img v-bind:src="btnUrl + supBtn">
        </div>
      </div>
      <div class="position_btn_container">
        <div class="position_btn">
          <img v-bind:src="btnUrl" alt="캐릭터 이미지">
        </div>
      </div>
    </div>
  </div>
</template>

<script scoped>
export default {
  data: function() {
    return {
      btnUrl: './src/assets/images/profile_make_btn/',
      micBtnLeft: 'mic_on_ON.png',
      micBtnRight: 'mic_off_OFF.png',
      topBtn: 'top_off.png',
      jgBtn: 'jg_off.png',
      midBtn: 'mid_off.png',
      adBtn: 'ad_off.png',
      supBtn: 'sup_off.png'
    }
  },
  methods: {
    micOn: function () {
      this.micBtnLeft = 'mic_on_ON.png';
      this.micBtnRight = 'mic_off_OFF.png';
      this.$emit('micOn');
    },
    micOff: function () {
      this.micBtnLeft = 'mic_on_OFF.png';
      this.micBtnRight = 'mic_off_ON.png';
      this.$emit('micOff');
    },
    topToggle: function () {
      if (this.topBtn === 'top_off.png') {
        this.topBtn = 'top_on.png';
        this.$emit('positionBtnTouch', 'topOn');
      } else if(this.topBtn === 'top_on.png'){
        this.topBtn = 'top_off.png';
        this.$emit('positionBtnTouch', 'topOff');
      }
    },
    jgToggle: function () {
      if (this.jgBtn === 'jg_off.png') {
        this.jgBtn = 'jg_on.png';
        this.$emit('positionBtnTouch', 'jgOn');
      } else if(this.jgBtn === 'jg_on.png'){
        this.jgBtn = 'jg_off.png';
        this.$emit('positionBtnTouch', 'jgOff');
      }
    },
    midToggle: function () {
      if (this.midBtn === 'mid_off.png') {
        this.midBtn = 'mid_main.png';
        this.$emit('positionBtnTouch', 'midOn');
      } else if(this.midBtn === 'mid_main.png'){
        this.midBtn = 'mid_off.png';
        this.$emit('positionBtnTouch', 'midOff');
      }
    },
    adToggle: function () {
      if (this.adBtn === 'ad_off.png') {
        this.adBtn = 'ad_on.png';
        this.$emit('positionBtnTouch', 'adOn');
      } else if(this.adBtn === 'ad_on.png'){
        this.adBtn = 'ad_off.png';
        this.$emit('positionBtnTouch', 'adOff');
      }
    },
    supToggle: function () {
      if (this.supBtn === 'sup_off.png') {
        this.supBtn = 'sup_on.png';
        this.$emit('positionBtnTouch', 'supOn');
      } else if(this.supBtn === 'sup_on.png'){
        this.supBtn = 'sup_off.png';
        this.$emit('positionBtnTouch', 'supOff');
      }
    }
  }
}
</script>

<style scoped>
.voice_area, .position_area {
  text-align: center;
}

.voice_btn_container {
  width: 40%;
  display: inline-block;
}

.voice_btn img, .position_btn img {
  width: 100%;
}

.position_btn_container {
  width: 26%;
  display: inline-block;
}
</style>