<template>
  <v-ons-toolbar>
    <div class="left">
    </div>
    <div class="page_name center">
      {{ pageName }}
    </div>
    <div class="right">
    </div>
  </v-ons-toolbar>
</template>

<script>
export default {
  data: function () {
    return {

    }
  },
  computed: {
    isVoiceOn: function () {
      return this.$store.state.isVoiceOn;
    },
    pageCount: function () {
      return this.$store.state.mainPageStackLength;
    },
    pageName: function () {
      let name = "";
      switch (this.pageCount) {
      case 0:
        name = "기본 정보 입력"
        break;
      case 1: 
        name = "티어 선택";
        break;
      case 2:
        name = "챔피언 선택";
        break;
      default:
        break;
      }
      return name;
    }
  }
}
</script>

<style scoped>

.page_name {
  font-weight: 800;
  font-size: 1.5em;
}

.left {
  width: 20%;
}

.idInput {
  width: 60%;
}

.center {
  text-align: center;
  width: 60%;
}

.right {
  text-align: center;
  width: 20%;
}

.voice_btn {
  font-size: 2em;
}

.voice_on {
  color:chartreuse;
}

.voice_off {
  color:red;
}

.ingame_id_show {
  color: black;
  font-weight: 800;
  font-size: 1.5em;
}

.change_btn {
  color: black;
}

</style>