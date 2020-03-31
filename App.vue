<template id="main">
  <v-ons-page>
    <transition name="mode-change" mode="out-in">
      <div v-if="appMode === 0">
        <start-view v-on:start="nextMode"></start-view>
      </div>

      <div v-if="appMode === 2">
        <profile-make-top-toolbar ></profile-make-top-toolbar>
        <profile-make-view v-on:profile_complete="nextMode"></profile-make-view>
      </div>

      <div v-if="appMode === 4">
        <top-toolbar></top-toolbar>
        <v-ons-tabbar position="bottom"
          :tabs="tabs"
          :visible="true"
          :index.sync="tabIdx"
        >
        </v-ons-tabbar>
      </div>
    </transition>
  </v-ons-page>
</template>

<script>
import StartView from './components/start/StartView.vue'
import TopToolbar from './components/common/TopToolbar.vue'
import ProfileMakeTopToolbar from './components/common/ProfileMakeTopToolbar.vue'
import ProfileMakeView from './components/profilemake/ProfileMakeView.vue'
import MessengerView from './components/tabpages/MessengerView.vue'
import SettingView from './components/tabpages/SettingView.vue'

import MainView from './components/main/MainView.vue'

/*
 *  input box 관련 js
 */

// (function() {
// // trim polyfill : https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/Trim
// 	if (!String.prototype.trim) {
// 		(function() {
// 			// Make sure we trim BOM and NBSP
// 			var rtrim = /^[\s\uFEFF\xA0]+|[\s\uFEFF\xA0]+$/g;
// 			String.prototype.trim = function() {
// 				return this.replace(rtrim, '');
// 			};
// 		})();
// 	}
// 		[].slice.call( document.querySelectorAll( 'input.input__field' ) ).forEach( function( inputEl ) {
// 		// in case the input is already filled..
// 		if( inputEl.value.trim() !== '' ) {
// 			classie.add( inputEl.parentNode, 'input--filled' );
// 		}
// 			// events:
// 		inputEl.addEventListener( 'focus', onInputFocus );
// 		inputEl.addEventListener( 'blur', onInputBlur );
// 	} );
// 		function onInputFocus( ev ) {
// 		classie.add( ev.target.parentNode, 'input--filled' );
// 	}
// 		function onInputBlur( ev ) {
// 		if( ev.target.value.trim() === '' ) {
// 			classie.remove( ev.target.parentNode, 'input--filled' );
// 		}
// 	}
// })();


export default {
  data: function () {
    return {
      profileCurPage: 0,
      loadingTimeout: 0,
      appMode: 0,
      /*
       * appMode 0 -> start view app 첫 시작 
       * appMode 2 -> profile card make view
       * appMode 4 -> main Page -> 로그인 후
       */
      tabIdx: 0,
      tabs: [
        {
          icon: 'ion-ios-home',
          label: 'ego',
          page: MainView,
          key: 'MainView'
        },
        {
          icon: 'fa-comments',
          label: 'Messenger',
          page: MessengerView,
          badge: 7,
          key: 'MessengerView'
        },
        {
          icon: 'ion-ios-settings',
          label: 'Settings',
          page: SettingView,
          key: 'SettingView'
        }
      ],
    }
  },
  methods: {
    nextMode: function (currentPage) {
      clearTimeout(this.loadingTimeout);
      this.appMode += 1;
      this.loadingTimeout = setTimeout(() => this.appMode += 1, 700);
    },
  },
  components: {
    StartView,
    ProfileMakeView,
    MessengerView,
    SettingView,
    TopToolbar,
    ProfileMakeTopToolbar,
    MainView
  } ,
  created: function () {
    let preset = JSON.parse(localStorage.getItem("preset1"));
    
    if(preset !== null) {
      this.appMode = 4;
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.page__content {
  background-color:#461f41;
}

.center {
  text-align: center;
}

.slide-fade-enter-active {
  transition: all .5s ease;
}
.slide-fade-leave-active {
  transition: all .5s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}
.slide-fade-enter, .slide-fade-leave-to
/* .slide-fade-leave-active below version 2.1.8 */ {
  transform: translateY(-20px);
  opacity: 0;
}

/*
 * fade
 */
.fade-enter-active, .fade-leave-active {
  transition: opacity .3s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}

/*
 * mode change
 */
.mode-change-enter-active, .mode-change-leave-active {
  transition: opacity .7s;
}
.mode-change-enter, .mode-change-leave-to {
  opacity: 0;
}

/*
 *  input box css
 */

input {
  font-size: 20px;
  margin-left: auto;
  margin-right: auto;
}

.input {
  width: 80%;
}

.input_area {
  width: 100%;
}


</style>
