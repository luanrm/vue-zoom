<template>
  <div></div>
</template>

<script>
import { ZoomMtg } from "@zoomus/websdk";
import axios from "axios";

const zoomJSLib='https://source.zoom.us/1.7.9/lib';
const zoomJSAVLib='/av'

ZoomMtg.setZoomJSLib(zoomJSLib, zoomJSAVLib);

ZoomMtg.preLoadWasm();
ZoomMtg.prepareJssdk();

export default {
  name: "Meeting",
  props: {
    msg: String
  },
  data() {
    return {
      signatureEndpoint: 'http://localhost:4000',
      apiKey: 'xu3asdfaJPaA_RJW2-9l5_HAaLA',
      meetingNumber: 123456789,
      leaveUrl: 'http://localhost:8080',
      userName: 'VueJS Zoom',
      userEmail: '', // required for webinar
      passWord: '', // if required
      role: 0 // 1 for host; 0 for attendee or webinar
    };
  },
  mounted() {
    this.getSignature();
  },
  methods: {
    startMeeting(signature) {

      ZoomMtg.init({
        leaveUrl: this.leaveUrl,
        isSupportAV: true,
        success: success => {
          console.log(success);

          ZoomMtg.join({
            signature: signature,
            meetingNumber: this.meetingNumber,
            userName: this.userName,
            apiKey: this.apiKey,
            userEmail: this.userEmail,
            passWord: this.passWord,
            success: success => {
              console.log(success);
            },
            error: error => {
              console.log(error);
            }
          });
        },
        error: error => {
          console.log(error);
        }
      });
    },

    getSignature() {
      axios
        .post(this.signatureEndpoint, {
          meetingNumber: this.meetingNumber,
          role: this.role
        })
        .then(response => {
          this.startMeeting(response.data.signature);
        })
        .catch(error => {
          console.log(error);
        });
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
