<template>
  <div class="login">
    <h1>Welcome back to Okta</h1>
    <div class="login--form">
      <div class="row">
        <label class="field-wrapper" for="login-email">
          <a class="btn" :href="uris.email">
            Sign In With Email
          </a>
        </label>
      </div>
      <div class="splitter">
        <span></span>
        <span>or</span>
        <span></span>
      </div>
      <div class="row">
        <div class="field-wrapper">
          <a class="btn social-btn" :href="uris.github">
            <i class="fa fa-github"></i> Continue with GitHub
          </a>
        </div>
      </div>
      <div class="row">
        <div class="field-wrapper">
          <a class="btn social-btn" :href="uris.google">
            <span class="google-logo"></span> Continue with Google
          </a>
        </div>
      </div>
      <div class="row goto-signup">
        Need an account?
        <SmartLink :item="{ link: '/signup/' }">Sign up</SmartLink>
      </div>
    </div>
    <div class="logo-wrapper">
      <CompanyLogos withHeading small />
    </div>
  </div>
</template>

<script>
import { getIdpUri } from "../util/uris";

export default {
  name: "Login",
  components: {
    CompanyLogos: () => import("../components/CompanyLogos"),
    SmartLink: () => import("../components/SmartLink"),
  },
  computed: {
    uris() {
      const { uris } = this.$site.themeConfig;

      return {
        email: "https://login.okta.com/",
        github: getIdpUri(uris, "github"),
        google: getIdpUri(uris, "google"),
      };
    },
  },
};
</script>
