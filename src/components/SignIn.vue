<template>
  <div id="app">
  <section>
    <div class="section-wrapper quick-switch">
      <div class="layout-twothirds-center">
        <input id="returnUrl" type="hidden" value="/">
        <input id="reauthenticate" type="hidden" value="">
        <div id="cdn-error" class="hidden error-message">
          <a href=""></a>
        </div>
        <div id="error" class="hidden quick-switch">
           <p class="error-message"> </p>
        </div>
        <div id="login-info">
           <p class="info-message hide-when-two-factor hidden"> </p>
        </div>
        <h1>Log in to Trello</h1>
        <div class="create-account quiet">
           or <a href="https://trello.com/signup" id="signup">create an account</a>
        </div>
        <div class="login-password-container   ">
           <form id="login-form" novalidate="novalidate" method="POST">
             <div class="login-password-container-email">
               <div class="hide-when-two-factor">
                 <label for="user">Email
                   <span class="quiet">(or username)</span>
                 </label>
                 <input type="email" name="user" id="user" autocorrect="off" spellcheck="false" autocapitalize="off" autofocus="autofocus" placeholder="e.g., e.hughes@downton.org.uk">
                 <label for="password">Password</label>
                 <input type="password" name="password" id="password" placeholder="e.g., ••••••••••••">
               </div>
               <div class="two-factor hidden">
                 <div class="two-factor-sms hidden">
                   We've sent a code to <b><span class="sms-number"></span></b>, it should get to you soon.
                 </div>
                 <div class="two-factor-sms-error hidden"> We tried to send a code to <b><span class="sms-number"></span></b>
                    but there was an error. You can <a id="start-over" href="https://trello.com/login?returnUrl=%2F#">try to login again</a> or enter a backup code.
                  </div>
                  <div class="two-factor-totp hidden"> Use the app on your mobile device to generate a code.
                  </div>
                  <br> <label>Two Factor Authentication Code
                    <input class="two-factor-sms two-factor-sms-error hidden" type="number" name="two-factor" autocomplete="off" id="sms" placeholder="e.g., 723110">
                    <input class="two-factor-totp hidden" type="number" name="two-factor" autocomplete="off" id="totp" placeholder="e.g., 723110">
                  </label>
                  <label style="display:inline;">
                    <input type="checkbox" id="remember" style="display:inline;position:relative;top:-2px;margin: 0 .3em .3em">  Don't ask for codes when I log in on this device
                  </label>
                </div>
                <input id="login" type="submit" class="button button-green" value="Log In">
                <div class="login-google-button hide-when-two-factor">
                  <div id="google-link" class="google-button" tabindex="0">
                    <span class="icon"></span>
                    <span class="label">Log in with Google</span>
                  </div>
                </div>
              </div>
            </form>
            <p class="quiet hide-when-two-factor"> <a href="https://trello.com/login/sso?returnUrl=%2F">Log in with SSO</a> </p>
            <span class="login-forget-password quiet hide-when-two-factor"> <a href="https://trello.com/forgot">Forgot your password?</a> </span>
            <br>
        </div>

        <div class="hidden">
            <form id="login-google" action="https://trello.com/authenticate_openid" method="post">
              <input type="hidden" name="openid_identifier" value="https://www.google.com/accounts/o8/id">
              <input type="hidden" name="provider" value="google">
              <input type="hidden" name="returnUrl" value="/">
              <input type="hidden" name="locale" id="login-google-locale" value="">
              <input type="hidden" name="confirmNew" value="true">
            </form>
           <form id="login-atlassian" action="https://trello.com/authenticate_openid" method="post">
             <input type="hidden" name="openid_identifier" value="https://id.atlassian.com/openid/v2/op">
             <input type="hidden" name="provider" value="atlassian">
             <input type="hidden" name="returnUrl" value="/">
             <input type="hidden" name="locale" id="login-atlassian-locale" value="">
             <input type="hidden" name="confirmNew" value="true">
           </form>
        </div>
      </div>
    </div>
  </section>

  <TrelloFooter></TrelloFooter>
  </div>
</template>

<script>
import TrelloFooter from './Trello_Footer.vue'

export default {
  'TrelloFooter' : TrelloFooter,
}
</script>

<style>
.quiet{color:#999}a.quiet,.quiet a{color:#999}a.quiet:hover,.quiet a:hover{color:#333}blockquote{padding-left:1em;border-left:1px solid #dcdcdc;margin-left:1em}label{display:block;margin:0 0 .4em}textarea,input{display:block;margin:0 0 1.2em}textarea,input[type="text"],input[type="email"],input[type="password"],input[type="number"],#user-type-container{background:#EDEFF0;border-radius:4px;border:1px solid #CDD2D4;-moz-box-sizing:border-box;box-sizing:border-box;padding:.5em;max-width:400px;width:100%}textarea:hover,input[type="text"]:hover,input[type="email"]:hover,input[type="password"]:hover,input[type="number"]:hover,#user-type-container:hover{border-color:#B6BBBF}textarea:focus,input[type="text"]:focus,input[type="email"]:focus,input[type="password"]:focus,input[type="number"]:focus,#user-type-container:focus{border-color:#A5ACB0;outline:none;box-shadow:0 0 6px #CDD2D4}textarea.error,input[type="text"].error,input[type="email"].error,input[type="password"].error,input[type="number"].error,#user-type-container.error{background:#FBEDEB;border:1px solid #EC9488}textarea.error:focus,input[type="text"].error:focus,input[type="email"].error:focus,input[type="password"].error:focus,input[type="number"].error:focus,#user-type-container.error:focus{box-shadow:0 0 6px #EC9488}input[type="button"]:focus,input[type="submit"]:focus{outline:none}input[type=number]::-webkit-inner-spin-button,input[type=number]::-webkit-outer-spin-button{-webkit-appearance:none;appearance:none;margin:0}.button{background:#CDD2D4;background:-webkit-gradient(linear, left top, left bottom, color-stop(0, #CDD2D4), to(#C4C9CC));background:linear-gradient(to bottom, #CDD2D4 0, #C4C9CC 100%);border-radius:.3em;box-shadow:0 2px 0 #4d4d4d;color:#4d4d4d;display:inline-block;font-weight:bold;margin-bottom:.8em;padding:.6em 1.3em;position:relative;text-decoration:none;border:0}.button:not([disabled]):focus,.button:not([disabled]):hover{background:#C4C9CC;background:-webkit-gradient(linear, left top, left bottom, color-stop(0, #C4C9CC), to(#B6BBBF));background:linear-gradient(to bottom, #C4C9CC 0, #B6BBBF 100%);color:#4d4d4d}.button:not([disabled]):active{background:#B6BBBF;background:-webkit-gradient(linear, left top, left bottom, color-stop(0, #B6BBBF), to(#A5ACB0));background:linear-gradient(to bottom, #B6BBBF 0, #A5ACB0 100%);color:#4d4d4d}.button[disabled]{background:#E2E4E6;box-shadow:none;color:#8c8c8c;cursor:default}.button-green{background:#61BD4F;background:-webkit-gradient(linear, left top, left bottom, color-stop(0, #61BD4F), to(#5AAC44));background:linear-gradient(to bottom, #61BD4F 0, #5AAC44 100%);box-shadow:0 2px 0 #3F6F21;color:#fff}.button-green:not([disabled]):focus,.button-green:not([disabled]):hover{background:#5AAC44;background:-webkit-gradient(linear, left top, left bottom, color-stop(0, #5AAC44), to(#519839));background:linear-gradient(to bottom, #5AAC44 0, #519839 100%);color:#fff}.button-green:not([disabled]):active{background:#519839;background:-webkit-gradient(linear, left top, left bottom, color-stop(0, #519839), to(#49852E));background:linear-gradient(to bottom, #519839 0, #49852E 100%);color:#fff}.button.mod-wide{padding-right:1.7em;padding-left:1.7em}.outline-link{border:1px solid;border-radius:.3em;display:inline-block;margin:.6em 0;padding:.6em 1em;text-decoration:none}.header-nav{padding:1em .75em 0}.header-nav-link,.header-nav-link:visited{border:1px solid rgba(0,0,0,0.45);border-radius:.3em;color:rgba(0,0,0,0.45);display:inline-block;font-size:.8em;padding:.4em 1.2em;margin:0 .25em .25em;text-decoration:none;vertical-align:top}.header-nav-link:hover{border-color:#4d4d4d;color:#4d4d4d}.header-nav-left{float:left}.header-nav-right{float:right}.body-header-nav-dark-background .header-nav-link{border-color:rgba(255,255,255,0.9);color:rgba(255,255,255,0.9)}.body-header-nav-dark-background .header-nav-link:hover{background-color:rgba(255,255,255,0.2);border-color:rgba(255,255,255,0.9);color:#fff}pre,code{background:#e6e6e6;border-radius:4px;padding:.2em .4em}code{display:inline-block}section{overflow:hidden;padding:0 1em;word-wrap:break-word}section img{display:block;margin:1em auto;max-width:100%}section h1:first-child,section h2:first-child,section h3:first-child,section h4:first-child,section h5:first-child,section h6:first-child{margin-top:1em}
.section-wrapper{max-width:540px;margin:0 auto}.page-fine-print section{font-size:16px;line-height:1.44em}.section-background-blue{background:#0079BF;color:#fff}.section-background-blue a{color:rgba(255,255,255,0.8)}.section-background-blue a:hover{color:#fff}.section-background-faded-blue{background-color:#E4F0F6}.section-background-gold{background-color:#EDEFF0;background-image:url(https://d2k1ftgv7pobq7.cloudfront.net/meta/p/res/images/68369975a2dc2deec3d9d233ccf82ae3/gold-backgrounds-ocean.png);background-size:cover;background-position:center}.section-background-gold a{color:rgba(77,77,77,0.8)}.section-background-gold a:hover{color:#4d4d4d}.section-background-gray{background-color:#EDEFF0}.section-background-business-class{background:#42548E;color:#fff}.section-background-business-class a:not(.button){color:rgba(255,255,255,0.8)}.section-background-business-class a:not(.button):hover{color:#fff}.section-recommend-banner{background:#FAF3C0;padding:1em;text-align:center}.section-recommend-banner-text{margin:0}.section-recommend-banner-image{height:30px;width:30px;vertical-align:top}footer{font-size:.8em;margin:4em 1em;text-align:center}footer ul{list-style:none;margin:.5em 0 0;padding:0}footer li{display:inline-block;margin:0 .4em}footer p{margin:.5em 0}.atlassian-logo-small{width:150px;display:inline-block;vertical-align:top;margin-top:1px}.atlassian-logo-small.white{display:none}.atlassian-white-logo .atlassian-logo-small.white{display:inline-block}.atlassian-white-logo .atlassian-logo-small.gray{display:none}.inline-image{display:inline-block;height:24px;margin:0;width:24px;vertical-align:text-top}.rounded-corners{border-radius:4px}.text-center{text-align:center}.inline-block{display:inline-block}.display-show-large{display:none}.error-message{border-radius:4px;background:#F5D3CE;border:1px solid #EB5A46;display:inline-block;padding:.5em 1em}.info-message{border-radius:4px;background:#FAF3C0;border:1px solid #F2D600;display:inline-block;padding:.5em 1em}@media only screen and (min-width:650px){section{padding:2em 1em}}@media only screen and (min-width:900px){html{font-size:20px}section{padding:4em 1em}section img{max-width:initial}.section-wrapper{margin:0 auto;max-width:1300px}.layout-grid-frame{margin:0 auto;max-width:890px;position:relative}.layout-twothirds-center{display:block;max-width:585px;margin:0 auto;position:relative}.layout-twothirds-left{max-width:585px}.layout-twothirds-right{margin-left:315px;width:585px}.display-show-large{display:inline-block}.layout-callout-far-right,.layout-callout-far-left,.layout-callout-right,.layout-callout-left{position:absolute;top:-3em}.layout-callout-right{left:640px}.layout-callout-left{right:640px}.layout-callout-up3{top:-6em}.layout-callout-up2{top:-5em}.layout-callout-up1{top:-4em}.layout-callout-down1{top:-2em}.layout-callout-down2{top:-1em}.layout-callout-down3{top:0}.layout-section-tall{padding:6em 1em}}.hidden{display:none !important;visibility:hidden}.visuallyhidden{border:0;clip:rect(0 0 0 0);height:1px;margin:-1px;overflow:hidden;padding:0;position:absolute;width:1px}.visuallyhidden.focusable:active,.visuallyhidden.focusable:focus{clip:auto;height:auto;margin:0;overflow:visible;position:static;width:auto}.invisible{visibility:hidden}.clearfix:before,.clearfix:after{content:" ";display:table}.clearfix:after{clear:both}@media print,(-webkit-min-device-pixel-ratio:1.25),(min-resolution:120dpi){}@media print{*{background:transparent !important;color:#000 !important;box-shadow:none !important;text-shadow:none !important}a,a:visited{text-decoration:underline}a[href]:after{content:" (" attr(href) ")"}abbr[title]:after{content:" (" attr(title) ")"}a[href^="#"]:after,a[href^="javascript:"]:after{content:""}pre,blockquote{border:1px solid #999;page-break-inside:avoid}thead{display:table-header-group}tr,img{page-break-inside:avoid}img{max-width:100% !important}p,h2,h3{orphans:3;widows:3}h2,h3{page-break-after:avoid}}.google-button{display:inline-block;background:#4285F4;color:#fff;width:auto;border-radius:2px;border:1px solid #4285F4;box-shadow:0 2px 2px #C4C9CC;white-space:nowrap}.google-button:hover{cursor:pointer;box-shadow:0 2px 2px #A5ACB0}.google-button:active{background:#3367D6;border:1px solid #3367D6}.google-button span.icon{background:url('https://d2k1ftgv7pobq7.cloudfront.net/meta/p/res/images/8215f6659adc202403198fef903a447e/sign-in-with-google.svg') white 12px 50% no-repeat;display:inline-block;border-radius:1px;vertical-align:middle;width:42px;height:42px}.google-button span.label{display:inline-block;vertical-align:middle;height:42px;line-height:42px;margin:0;padding:0 12px;font-size:14px;font-weight:bold;font-family:'Roboto',sans-serif}.login-form .google-button{background:#fff;color:#4d4d4d;box-shadow:0 2px 2px rgba(0,0,0,0.2);margin-bottom:32px;border:0}.login-form .google-button:hover{cursor:pointer;box-shadow:0 3px 3px rgba(0,0,0,0.4)}.login-form .google-button:active{background:#EEEEEE;border:0}.login-form .google-button span.label{padding:0 12px 0 0}.login-form .google-button span.icon{border-radius:0}.section-home-login{padding:2em 1em 4em;text-align:center}.section-home-login .info-message{color:#777777}.section-home-login input#user,.section-home-login input#password{color:#666}.login-password-container-email{text-align:left}.login-forget-password{margin-left:.5em}.section-everything{padding-bottom:0}.section-everything img{margin-bottom:0;max-width:100%}.layout-company-logos img{display:inline-block;margin:0 1em 1em;height:30px}.app-store-link{display:inline-block;margin:.4em 1em 0 0;padding:0;vertical-align:top}.app-store-link img{height:54px;margin:0}.app-link-all{margin:.4em 0 0}.login-form{width:430px}.login-form input[type="text"],.login-form input[type="password"],.login-form input[type="email"]{max-width:430px;color:#000}.login-form button{margin:0}.no-script-show{display:none}@media only screen and (min-width:900px){.layout-fill-image img{-moz-box-sizing:border-box;box-sizing:border-box;max-width:100%;padding:2em 3em 2em}.section-everything img{margin-top:2em}.layout-company-logos img{height:60px}.section-love-header{padding-bottom:2em}}</style>   <style>@font-face{font-family:'Charlie Display';src:url(https://d2k1ftgv7pobq7.cloudfront.net/meta/p/res/fonts/charlie-sans/charlie-display/7c1c0a53957fc3b9f2716e8f26d50cf1/Charlie_Display-Regular.woff) format("woff"),url(https://d2k1ftgv7pobq7.cloudfront.net/meta/p/res/fonts/charlie-sans/charlie-display/b4c3881bee93dfe1488688bb9d4d8e49/Charlie_Display-Regular.woff2) format("woff2");font-weight:400;font-style:normal}@font-face{font-family:'Charlie Display';src:url(https://d2k1ftgv7pobq7.cloudfront.net/meta/p/res/fonts/charlie-sans/charlie-display/9173dc9a5a19f693f05f5986971b8b6c/Charlie_Display-Italic.woff) format("woff"),url(https://d2k1ftgv7pobq7.cloudfront.net/meta/p/res/fonts/charlie-sans/charlie-display/d93c5598b0534dc3a40ecececcc9de90/Charlie_Display-Italic.woff2) format("woff2");font-weight:400;font-style:italic}@font-face{font-family:'Charlie Display';src:url(https://d2k1ftgv7pobq7.cloudfront.net/meta/p/res/fonts/charlie-sans/charlie-display/aa4aa85c7ef84dd4cb06bba4cd08a1b6/Charlie_Display-Semibold.woff) format("woff"),url(https://d2k1ftgv7pobq7.cloudfront.net/meta/p/res/fonts/charlie-sans/charlie-display/5df3e495e418541d4ee58565d65300a3/Charlie_Display-Semibold.woff2) format("woff2");font-weight:500;font-style:normal}@font-face{font-family:'Charlie Display';src:url(https://d2k1ftgv7pobq7.cloudfront.net/meta/p/res/fonts/charlie-sans/charlie-display/a1ed6acc62220d32d87a82a8df77193d/Charlie_Display-Semibold_Italic.woff) format("woff"),url(https://d2k1ftgv7pobq7.cloudfront.net/meta/p/res/fonts/charlie-sans/charlie-display/819212d1023047c5cbc4bf7087a22683/Charlie_Display-Semibold_Italic.woff2) format("woff2");font-weight:500;font-style:italic}@font-face{font-family:'Charlie Text';src:url(https://d2k1ftgv7pobq7.cloudfront.net/meta/p/res/fonts/charlie-sans/charlie-text/b7e8ae700922f44a87cf9bfa816f47f3/Charlie_Text-Regular.woff) format("woff"),url(https://d2k1ftgv7pobq7.cloudfront.net/meta/p/res/fonts/charlie-sans/charlie-text/b2fe1098e251238a45ea8d199d04723e/Charlie_Text-Regular.woff2) format("woff2");font-weight:400;font-style:normal}@font-face{font-family:'Charlie Text';src:url(https://d2k1ftgv7pobq7.cloudfront.net/meta/p/res/fonts/charlie-sans/charlie-text/3161515033c7d26793fd0aaae47f24b9/Charlie_Text-Italic.woff) format("woff"),url(https://d2k1ftgv7pobq7.cloudfront.net/meta/p/res/fonts/charlie-sans/charlie-text/f4371c9195626a4e38ab56673b51f638/Charlie_Text-Italic.woff2) format("woff2");font-weight:400;font-style:italic}@font-face{font-family:'Charlie Text';src:url(https://d2k1ftgv7pobq7.cloudfront.net/meta/p/res/fonts/charlie-sans/charlie-text/f7510eaae5eb4e52cf90295b6a217659/Charlie_Text-Semibold.woff) format("woff"),url(https://d2k1ftgv7pobq7.cloudfront.net/meta/p/res/fonts/charlie-sans/charlie-text/1c6e2a15a0f304ec8bef45481a75a07c/Charlie_Text-Semibold.woff2) format("woff2");font-weight:500;font-style:normal}@font-face{font-family:'Charlie Text';src:url(https://d2k1ftgv7pobq7.cloudfront.net/meta/p/res/fonts/charlie-sans/charlie-text/bdcc5e50c64eb53e33d53cbb97dcdfae/Charlie_Text-Semibold_Italic.woff) format("woff"),url(https://d2k1ftgv7pobq7.cloudfront.net/meta/p/res/fonts/charlie-sans/charlie-text/9182af6e9b3e010d663a2b6b25bc5904/Charlie_Text-Semibold_Italic.woff2) format("woff2");font-weight:500;font-style:italic}
</style>
