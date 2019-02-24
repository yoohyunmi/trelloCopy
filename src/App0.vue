<template>
  <div id="app">
    <!-- 01. Header Start  -->
    <div class="global-header mod-trello-blue">
      <div class="container">
        <!-- Trello Home 로고 -->

        <div class="global-header-section mod-left">
          <a href="/" class="global-header-section-logo">
              <img src="./assets/files/trello-logo-white.svg" class="global-header-section-logo-image">
          </a>
        </div>

        <!-- 로그인, 가입 버튼 -->
        <div class="global-header-section mod-right">
<!--          <a href="/SignIn" class="header-button-secondary">Log In</a> -->
          <a class="header-button-secondary"><router-link to="/SignIn">Log In</router-link></a>
          <a href="/signup" class="header-button-primary">Sign Up</a>
        </div>
      </div>
    </div>
    <!-- 01. Header End -->

    <!-- 02. 소개페이지 Start -->
    <!-- ??? 솔직히 왜 hero이며, 헤더랑 같은 섹션을 공유하는지 잘 모르겠음... -->
    <section id="hero">
      <div class="layout-two-col">
        <div class="hero-text"></div>
        <div class="hero-image">
          <img src="./assets/files/hero-a.svg" width="582">
        </div>
      </div>
    </section>
    <!-- 02. 소개페이지 End -->


    <!-- 03. 협업페이지 Start -->
    <section id="collaborate">
      <div class="layout-two-col">
        <div class="layout-two-text"></div>
        <div class="layout-two-image"></div>
      </div>
    </section>
    <!-- 03. 협업페이지 End -->

    <!-- 04. 협업 소개페이지 Start -->
    <section id="teams">
      <div class="layout-two-col">
        <div class="layout-two-text"></div>
        <div class="layout-two-image"></div>
      </div>
    </section>
    <!-- 04. 협업 소개페이지 End -->

    <!-- 05. 데모페이지 Start -->
    <section id="demo">
      <div class="container">
        <div class=""></div>
        <div class=""></div>
      </div>
    </section>
    <!-- 05. 데모페이지 End -->

    <!-- 06. 특징페이지 Start -->
    <section id="features">
      <div class="container">
        <div class="text"></div>
        <div class="">
          <div></div> <!-- Work With Any Team -->
          <div></div> <!-- A Productivity Platform -->
          <div></div> <!-- Always In Sync -->
        </div>
      </div>
    </section>
    <!-- 06. 특징페이지 End -->


    <!-- 07. Bottom Start -->
    <div id="bottom-gradient">
      <section class="work-smarter"></section> <!-- Work smarter with Trello -->
      <section class="get-started"></section>  <!-- Start Planning Today -->

    </div>
    <!-- 07. Bottom End -->

    <TrelloFooter></TrelloFooter>

      <section>
        <router-view></router-view>
      </section>

  </div>

</template>

<script>
import TrelloFooter from './components/Trello_Footer.vue';
import Vue from 'vue'
import Router from 'vue-router'
import routes from './main'

export default ({
  routes,
  components :{
    'TrelloFooter' : TrelloFooter
  }
});


</script>
