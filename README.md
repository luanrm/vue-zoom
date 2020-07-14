
# Zoom Web SDK Sample VueJS

## Installation

To get started, clone the repo:

`$ git clone https://github.com/luanrm/vue-zoom.git`

## Setup

1. Once cloned, navigate to the `vue-zoom` directory:

   `$ cd vue-zoom`

1. Then install the dependencies:

   `$ npm install`

1. Open the `vue-zoom` directory in your code editor.

1. Open the `src/components/Meeting.vue` file, and enter values for the variables:

   | Variable                   | Description |
   | -----------------------|-------------|
   | signatureEndpoint          | Required, the endpoint url that returns a signature. [Get a signature endpoint here.](https://github.com/zoom/websdk-sample-signature-node.js) |
   | apiKey                   | Required, your Zoom JWT App API Key. [You can get yours here](https://marketplace.zoom.us/develop/create). |
   | meetingNumber                   | The Zoom Meeting / webinar number. |
   | role                   | Required, 0 to join the meeting / webinar, 1 to start the meeting. |
   | leaveUrl                   | Required, the url the user is taken to once the meeting is over. |
   | userName                   | Required, A name for the user joining / starting the meeting / webinar. |
   | userEmail                   | Optional, the user joining / starting the meeting / webinar. |
   | passWord                   | Optional, meeting password. Leave as empty string if the meeting does not require a password. |

   Example:

   ```js
   signatureEndpoint = 'http://localhost:4000'
   apiKey = 'xu3asdfaJPaA_RJW2-9l5_HAaLA'
   meetingNumber = 123456789
   role = 0
   leaveUrl = 'http://localhost:8080'
   userName = 'Vue Zoom'
   userEmail = ''
   password = ''
   ```

1. Save `Meeting.vue`.

1. Run the app:

   `$ npm run serve`

## Usage

1. Navigate to http://localhost:8080.
