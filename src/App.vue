<script setup>
import {ref} from 'vue'
import {BILIBILISPACE, YOUTUBESPACE, GITHUBSPACE, QINIUYUNURL} from './const.js'

let userLanguage = navigator.language || navigator.userLanguage;
let localLang = localStorage.getItem("isZh");
let isZh = ref(true)
let isDetail = ref(false)
if (userLanguage.indexOf('zh') > -1) {
  isZh.value = true;
} else {
  isZh.value = false;
}
localLang && localLang === 'true' ? isZh.value = true : isZh.value = false;

function changeLanguage(lang) {
  if (lang === 'zh') {
    isZh.value = true;
    localStorage.setItem("isZh", isZh.value + '');
    return
  }
  isZh.value = false;
  localStorage.setItem("isZh", isZh.value + '');

}
function showDetail(flag) {
  isDetail.value = flag;
}

console.log("浏览器语言:", userLanguage);
</script>

<template>
  <div class="language">
    <span>
          <span :class="{ lang: true, 'focus-lang': isZh }" @click="changeLanguage('zh')">中文 </span>
          <span :class="{ lang: true, 'focus-lang': !isZh }" @click="changeLanguage('en')"> English</span>
    </span>

  </div>
  <div class="avatar">
    <span class="avatar-img"></span>
  </div>
  <div class="name-me"> {{ isZh ? '陈明明' : 'Mannix Chen' }}</div>
  <div class="desc"> {{ isZh ? '视频创作者, 程序员 ' : 'Filmmaker, Programmer' }} <span @click="showDetail" class="show-more">→</span></div>
  <div class="related">
    <!--    <span>-->
    <!--    <a> PORTFOLIO</a>-->

    <!--    </span>-->
    <span>    <a :href="BILIBILISPACE" target="_blank">
      BILIBILI
    </a></span>
    <span>    <a :href="YOUTUBESPACE" target="_blank">
      YOUTUBE
    </a></span>
    <span>
          <a :href="GITHUBSPACE" target="_blank">
          GITHUB
        </a>
    </span>


  </div>
  <div v-if="isDetail" id="person-info">
    <div style="text-align: right; color: white;" class="close-button"><span class="close-detail" @click="showDetail(false)">X</span></div>
    <div class="person-achievement">
      {{isZh ? "努力中..." : "On my way..."}}
    </div>
  </div>
  <!--  <div class="buttons">-->
  <!--    <div class="inner-buttons">-->
  <!--      <span>商务咨询</span>-->
  <!--      <span>联系我</span>-->
  <!--    </div>-->
  <!--  </div>-->
</template>

<style scoped>
#person-info {
  width: 350px;
  height: 350px;
  padding: 10px;
  background-color:  rgba(0, 0, 0, .8);
  position: absolute;
  left: 50%;
  top: 40%;
  transform: translate(-50%, -50%);
  border-radius: 5px;
}
.close-detail {
  display: inline-block;
  width: 30px;
  height: 30px;
  line-height: 30px;
  text-align: center;
}
.close-button:hover{
  scale: 1;
  cursor:pointer;
}
.person-achievement {
  color: #9C9D9D;
  margin-top: 10px;
  text-align: left;
}

.focus-lang {
  scale: 1.3;
}

.lang {
  display: inline-block;
  margin-right: 10px;
}

.language {
  text-align: right;
  color: #cccccc;
}

.avatar {
  margin-top: 3rem;
  color: #ccc;
}

.avatar-img {
  background: center / cover no-repeat url("http://cdn.gnim.top/mannixchen.com/AVATAR.jpg") rgba(0, 0, 0, .7);
  display: inline-block;
  height: 100px;
  width: 100px;
  border-radius: 100px;
}

.show-more {
  display: inline-block;
}

.show-more:hover {
  color: #fff;
  filter: drop-shadow(0 0 2em rgba(255, 255, 255, 0.93));
  scale: 1.3;
}

.name-me {
  margin-top: 30px;
  font-size: 4rem;
  color: rgba(249, 249, 249, 0.95);
  font-weight: 900;
  line-height: 1.2em;

}

.desc {
  font-weight: 200;
  margin-top: 10px;
  font-size: 2rem;
  color: rgba(249, 249, 249, 0.87);
  line-height: 1.2em;
}

.related {
  display: flex;
  justify-content: space-between;
  color: #F9F9F9;

}

.related span {
  display: inline-block;
  width: 265px;
  font-size: 3rem;
  color: rgba(249, 249, 249, 0.88);
  font-weight: 600;
  line-height: 8em;
}

.related span a {
  font-weight: 600;
}

.related a:hover {
  color: #fff;
  filter: drop-shadow(0 0 2em rgba(255, 255, 255, 0.48));
}

.buttons {
  padding: 0 100px;
}

.inner-buttons {
  display: flex;
  justify-content: space-around;
  color: #F9F9F9;
}

.inner-buttons span {
  display: inline-block;
  width: 150px;
  line-height: 3rem;
  background-color: #5C7AC9;
  font-family: Sans-serif;
  font-weight: 600;
  border-radius: 3px;
}

.inner-buttons span:hover {
  color: #fff;
  filter: drop-shadow(0 0 1em rgba(92, 122, 201, 0.22));
  cursor: pointer;
}

.logo {
  height: 1em;
  padding: .5em;
  will-change: filter;
  transition: filter 300ms;
}

.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}

.logo.bilibili:hover {
  filter: drop-shadow(0 0 2em #F9F9F9);
}

.logo.youtube:hover {
  filter: drop-shadow(0 0 2em #F9F9F9);
}

@media screen and (max-width: 850px) {
  .inner-buttons {
    display: flex;
    justify-content: space-between;
    color: #F9F9F9;
    flex-direction: column;
    align-items: center;
  }

  .inner-buttons span {
    margin-top: 20px;
  }

  .related {
    display: flex;
    color: #F9F9F9;
    flex-direction: column;
    align-items: center;

  }

  .related span {
    line-height: 2em;
  }
}
</style>
