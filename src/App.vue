<template>
  <div id="app">
    <!-- 01. Header Start  -->
    <div class="global-header mod-trello-blue mod-dark-background u-clearfix scroll" data-track-group="Global Header">
      <div class="container">
        <!-- Trello Home 로고 -->

        <div class="global-header-section mod-left">
          <a href="/" class="global-header-section-logo">
              <img alt="Home" src="./assets/files/trello-logo-white.svg" class="global-header-section-logo-image">
          </a>
        </div>

        <!-- 로그인, 가입 버튼 -->
        <div class="global-header-section mod-right">
<!--          <a href="/SignIn" class="header-button-secondary">Log In</a> -->
          <a class="header-button-secondary"><router-link to="/SignIn">Log In</router-link></a> <!--  <a href="/login?returnUrl=%2F"  -->
          <a href="https://trello.com/signup" class="header-button-primary">Sign Up</a>
        </div>
      </div>
    </div>
    <!-- 01. Header End -->

    <!-- 02. 소개페이지 Start -->
    <!-- ??? 솔직히 왜 hero이며, 헤더랑 같은 섹션을 공유하는지 잘 모르겠음... -->
    <section id="hero" class="dark-background">
      <div class="layout-two-col">
        <div class="hero-text">
          <h1>Trello lets you work more collaboratively and get more done.</h1>
          <p class="big">Trello’s boards, lists, and cards enable you to organize and prioritize your projects in a fun, flexible and rewarding way.</p>
          <p><a class="button-primary big">Sign Up - It's Free!</a></p>
        </div>
        <div class="hero-image">
          <img src="./assets/files/hero-a.svg" width="582">
        </div>
      </div>
    </section>
    <!-- 02. 소개페이지 End -->


    <!-- 03. 협업페이지 Start -->
    <section id="collaborate">
      <div class="layout-two-col">
        <div class="layout-two-text">
          <h2>Work with any team</h2>
          <p>Whether it’s for work, a side project or even the next family vacation, Trello helps your team stay organized.</p>
          <p><a href="https://trello.com/signup" class="button-secondary">Start doing →</a></p>
        </div>
        <div class="layout-two-image">
          <img src="./assets/files/updated-layouts-board.png" width="766" height="565">
        </div>
      </div>
    </section>
    <!-- 03. 협업페이지 End -->

    <!-- 04. 협업 소개페이지 Start -->
    <section id="teams">
      <div class="layout-two-col">
        <div class="layout-two-image">
          <img src="./assets/files/updated-layouts-mobile.png" width="618" height="565">
        </div>
        <div class="layout-two-text">
          <h2>Information at a glance</h2>
          <p>Dive into the details by adding comments, attachments, due dates, and more directly to Trello cards. Collaborate on projects from beginning to end.</p>
        </div>
      </div>
    </section>
    <!-- 04. 협업 소개페이지 End -->

    <!-- 05. 데모페이지 Start -->
    <section id="demo">
      <div class="container">
        <div class="layout-centered">
          <div class="layout-centered-content">
          </div>
        </div>
        <div id="carousel">
          <button class="slick-prev slick-arrow" aria-label="Previous" type="button" style="display: block;">Previous</button>
          <div class="slick-list draggable">

          </div>
          <button class="slick-next slick-arrow" aria-label="Next"  type="button" style="display: block;">Next</button>
          <ul class="slick-dots" style="display: block;" role="tablist">
            <li class="slick-active" role="presentation"></li>
          </ul>
        </div>
      </div>
    </section>
    <!-- 05. 데모페이지 End -->

    <!-- 06. 특징페이지 Start -->
    <section id="features">
      <div class="container">
        <div class="layout-centered">
          <div class="layout-centered-content">
            <h2>Trello your way</h2>
            <p>Use Trello the way your team works best. We’ve got the flexibility &amp; features to fit any team’s style.</p>
            <div class="layout-three-col">
              <div><!-- Work With Any Team -->
                <div class="img img-collaborate">
                  <img src="./assets/files/updated-layouts-collab.png" width="270">
                </div>
                <h3>Work With Any Team</h3>
                <p class="small">Whether it’s for work, a side project or even the next family vacation, Trello helps your team stay organized.</p>
                <p class="cta"><a class="button mod-no-margin" href="https://trello.com/teams">Build Your Dream Team</a></p>
              </div>
              <div><!-- A Productivity Platform -->
                <div class="img img-apps">
                  <img src="./assets/files/updated-layouts-platform.png" width="270">
                </div>
                <h3>A Productivity Platform</h3>
                <p class="small">Integrate the apps your team already uses directly into your workflow. Power-Ups turn Trello boards into living applications to meet your team's unique business needs.</p>
                <p class="cta"><a class="button mod-no-margin" href="">Power-Up Your Workflow</a></p>
              </div>
              <div><!-- Always In Sync -->
                <div class="img img-sync">
                  <img src="./assets/files/updated-layouts-sync.png" width="270">
                </div>
                <h3>Always In Sync</h3>
                <p class="small">No matter where you are, Trello stays in sync across all of your devices. Collaborate with your team anywhere, from sitting on the bus to sitting on the beach.</p>
                <p class="cta app-store">
                  <a href=""><img src="./assets/files/btn-appstore-black.png"></a>
                  <a href=""><img src="./assets/files/btn-playstore-black.png"></a>
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    <!-- 06. 특징페이지 End -->


        <!-- 07. Bottom Start -->
        <div id="bottom-gradient">
          <!-- Work smarter with Trello -->
          <section id="work-smarter" class="layout-centered dark-background">
            <div class="container text-center">
              <div class="layout-centered-content">
                <h2>Work smarter with Trello</h2>
                <p class="big">Companies of all shapes and sizes use Trello.</p>
              </div>
              <div class="logo-container">
                <img src="./assets/files/logo-adobe.svg" width="165" height="37">
                <img src="./assets/files/logo-kickstarter.svg" width="207" height="24">
                <img src="./assets/files/logo-national-geographic.svg" width="166" height="46">
                <img src="./assets/files/logo-google.svg" width="143" height="46">
                <img src="./assets/files/logo-fender.svg" width="153" height="55">
              </div>
              <div class="layout-centered-content">
                <p>
                  <a href="" class="button-secondary">Find out how -></a>
                </p>
              </div>
            </div>
          </section>
          <!-- Start Planning Today -->
          <section id="get-started">
            <div class="container text-center">
              <div class="layout-centered-content">
                <h2>Start Planning Today</h2>
                <p>
                  "Sign up and become one of the millions of people around the world using Trello to get more done."
                </p>
                <a href="" class="button-primary">Get Started - It's Free!</a>
              </div>
            </div>
          </section>
          <TrelloFooter></TrelloFooter>
        </div>
        <!-- 07. Bottom End -->
  </div>

</template>
<script>
import TrelloFooter from './components/Trello_Footer.vue';
import SignIn from './components/SignIn.vue';
import Home from './App.vue';
//import VueRouter from 'vue-router'
/*
Vue.use(VueRouter)
const router = new VueRouter({
  routes: [
    { path: '/', component: Home },
    { path: '/SignIn', component: SignIn }
  ]
})
*/
export default ({
  //router,
  component: {
    TrelloFooter,
    SignIn,
    Home
  }
});


</script>
