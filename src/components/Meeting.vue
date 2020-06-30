<template>
  <div class="ReactModal__Body--open">
    <!-- added on import -->
    <div id="zmmtg-root"></div>
    <div id="aria-notify-area"></div>

    <!-- added on meeting init -->
    <div class="ReactModalPortal"></div>
    <div class="ReactModalPortal"></div>
    <div class="ReactModalPortal"></div>
    <div class="ReactModalPortal"></div>
    <div class="global-pop-up-box"></div>
    <div class="sharer-controlbar-container sharer-controlbar-container--hidden"></div>
  </div>
</template>

<script>
import { ZoomMtg } from "@zoomus/websdk";
export default {
  name: "Meeting",
  props: {
    msg: String
  },
  mounted() {
    this.ZoomInit();
  },
  methods: {
    ZoomInit() {
      ZoomMtg.setZoomJSLib(
        "https://dmogdx0jrul3u.cloudfront.net/1.7.9/lib",
        "/av"
      );
      ZoomMtg.preLoadWasm();
      ZoomMtg.prepareJssdk();

      const meetConfig = {
        apiKey: "",
        meetingNumber: "123456789",
        leaveUrl: "http://192.168.1.102:8080/",
        userName: "Firstname Lastname",
        userEmail: "firstname.lastname@yoursite.com", // required for webinar
        passWord: "password", // if required
        role: 0 // 1 for host; 0 for attendee or webinar
      };

      ZoomMtg.init({
        leaveUrl: meetConfig.leaveUrl,
        isSupportAV: true,
        success: function() {
          ZoomMtg.join({
            signature: "cripto",
            apiKey: meetConfig.apiKey,
            meetingNumber: meetConfig.meetingNumber,
            userName: meetConfig.userName,
            // Email required for Webinars
            userEmail: meetConfig.userEmail,
            // password optional; set by Host
            password: meetConfig.passWord
          });
        },
        error(res) {
          console.log(res);
        }
      });
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
