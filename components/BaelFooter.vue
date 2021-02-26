<template>
  <footer class="fill-gray-lighter xs-text-6 md-text-5">
    <div class="r no-gap">
      <div v-if="pagination.active" class="c-12 xs-text-left xs-p2">
        <lazy-bael-pagination :pagination="pagination" />
      </div>
      <div
        class="xs-text-left xs-p2 xs-border xs-border-right-none xs-border-bottom-none"
        :class="signupAboutSize"
      >
        <div class="item">
          <div v-if="siteDescription" class="footer__heading xs-mb2">About</div>
          <p v-if="siteDescription">{{siteDescription}}</p>
        </div>
      </div>
      <div
        v-if="signupBoolean"
        class="c-25 xs-text-left xs-p2 xs-border xs-border-right-none xs-border-bottom-none"
      >
        <lazy-send-grid />
      </div>
      <div
        class="xs-text-left xs-p2 xs-border xs-border-right-none xs-border-bottom-none"
        :class="signupAboutSize"
      >
        <div class="item">
          <div v-if="connectData" class="footer__heading xs-mb2">Connect</div>
          <ul v-if="connectData" class="list-unstyled">
            <li v-for="(c,i) in connectData" :key="i">
              <a :href="c.url">{{c.name}}</a>
            </li>
          </ul>
        </div>
      </div>
      <div
        class="xs-text-left xs-p2 xs-border xs-border-right-none xs-border-bottom-none"
        :class="signupAboutSize"
      >
        <div class="item">
          <div class="footer__heading xs-mb2">Prayer request</div>

				Please be blessed as you relax and listen.
          
          </a>
        </div>
      </div>
      <div class="c-12 xs-text-left xs-p2 xs-border xs-border-right-none xs-border-bottom-none">
        <div class="item xs-text-6">
          Please have a Bible open while you listen.   You can get access to almost every one online for free from <a href="https://www.BibleGateway.com">Bible Gateway</a>.   We use the WEB version in our Scripture publication for the avoidance of copyright issues.  Our family is currently enjoying the International Children's Bible, (ICB) for its clarity and trustworthiness, and this is partially read out within the podcasts.
        </div>
      </div>
    </div>
  </footer>
  <iframe src="https://www.podbean.com/media/player/multi?playlist=http%3A%2F%2Fplaylist.podbean.com%2F11038968%2Fplaylist_multi.xml&amp;vjs=1&amp;size=430&amp;skin=1&amp;episode_list_bg=%23ffffff&amp;bg_left=%23000000&amp;bg_mid=%230c5056&amp;bg_right=%232a1844&amp;podcast_title_color=%23c4c4c4&amp;episode_title_color=%23ffffff&amp;auto=0&amp;share=1&amp;fonts=Helvetica&amp;download=1&amp;rtl=0&amp;show_playlist_recent_number=10" title="BIBLE IN TEN" width="100%" height="430" scrolling="no" style="border: none;"></iframe>
</template>

<script>
export default {
  data() {
    return {};
  },
  methods: {},
  computed: {
    pagination() {
      return this.$store.state.pagination;
    },
    version() {
      return process.env.BAEL_VERSION || false;
    },
    signupAboutSize: function () {
      return {
        "c-25": this.signupBoolean,
        "c-4": !this.signupBoolean,
      };
    },
    connectData() {
      return this.$store.state.connect;
    },
    siteDescription() {
      return this.$store.state.info.sitedescription;
    },
    signupBoolean() {
      return this.$store.state.info.emailsignup;
    },
  },
};
</script>

<style>
.text-input {
  max-width: 100%;
}
.small-txt {
  font-size: 80%;
}
footer .item:hover .footer__heading {
  color: rgba(119, 119, 119, 0.6);
  transition: 0.2s color ease-in-out;
}
.footer__heading {
  max-width: 100%;
  pointer-events: none;
  color: rgba(119, 119, 119, 0.4);
  font-weight: 800;
  font-size: 85%;
  transition: 0.1s color ease-in-out;
}
.pagination__button--disabled {
  pointer-events: none;
}
</style>
