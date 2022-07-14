<script setup>
</script>

<template>
<html>
<head>
    <meta charset="UTF-8" />
    <link rel="icon" href="/favicon.ico" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="preconnect" href="https://fonts.gstatic.com">
    <link
        href="https://fonts.googleapis.com/css2?family=Open+Sans:ital,wght@0,300;0,400;0,600;0,700;0,800;1,300;1,400;1,600;1,700;1,800&display=swap"
        rel="stylesheet">
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta2/dist/css/bootstrap.min.css" rel="stylesheet"
        integrity="sha384-BmbxuPwQa2lc/FVzBcNJ7UAyJxM6wuqIj61tLrc4wSX0szH/Ev+nYRRuWlolflfl" crossorigin="anonymous">
    <title>Instructions/Overview</title>
</head>

<body>
    <!-- Title -->
    <nav class="navbar navbar-expand-lg navbar-light bg-topbar">
        <br />
        <br />
        <div class="container-fluid">
            <div class="row">&nbsp;</div>
            <div class="row">
                <div class="col-12 text-center">
                    <h2><b>MorphGAN Evaluation Questions</b></h2>
                </div>
            </div>
            <div class="row">&nbsp;</div>
        </div>
    </nav>

    <!-- Begin -->
    <div class="container-fluid" style="width: 100%">

        <div class="row">&nbsp;</div>
        <div class="row">
            <div class="col-1">&nbsp;</div>
            <div class="col-10">
                <h4><b><u>1.Instructions</u></b></h4>
            </div>
            <div class="col-1">&nbsp;</div>
        </div>

        <div class="row">&nbsp;</div>
        <div class="row">
            <div class="col-1">&nbsp;</div>
            <div class="col-10">
                Thank you for participating in this listening test.<br> 
                Over the next few screens on this web-interface you will be presented with few sounds and asked few questions regarding them.  
                Please ensure you are seated in a quite place with no disturbances for the entirety of this test.
            </div>
            <div class="col-1">&nbsp;</div>
        </div>

        <div class="row">&nbsp;</div>
        <div class="row">
            <div class="col-1">&nbsp;</div>
            <div class="col-10">
                The <span style="color:red"><b>primary aim</b></span> of this listening test is to differentiate between <b>audio morphs</b> and 
                <b>mixes/cross-fades.</b>
            </div>
            <div class="col-1">&nbsp;</div>
        </div>

        <div class="row">&nbsp;</div>
        <div class="row">
            <div class="col-1">&nbsp;</div>
            <div class="col-10">
                In each trial in this test, you will be presented with few interpolated sounds and asked to evaluate if they are <b>audio morphs</b> or
                <b>mixes/cross-fades.</b>
            </div>
            <div class="col-1">&nbsp;</div>
        </div>

        <div class="row">&nbsp;</div>
        <div class="row">
            <div class="col-1">&nbsp;</div>
            <div class="col-10">
                This test should take approximately <u>1 hour</u> to complete.
            </div>
            <div class="col-1">&nbsp;</div>
        </div>

        <div class="row">&nbsp;</div>
        <div class="row">&nbsp;</div>

        <div class="row">
            <div class="col-1">&nbsp;</div>
            <div class="col-10">
                This listening test is composed of the following sections:
            </div>
            <div class="col-1">&nbsp;</div>
        </div>

        <div class="row">&nbsp;</div>
        <div class="row">
            <div class="col-1">&nbsp;</div>
            <div class="col-10">
                1. Instructions (This section) <br>
                2. Examples of audio morphs <br>
                3. Pre-test <br>
                4. Pre-survey <br>
                5. Individual listening trials <br>
                6. Comparative listening trials <br>
                7. Post-survey
            </div>
            <div class="col-1">&nbsp;</div>
        </div>

    </div>

</body>
</html>
</template>

<script>
import { mapActions } from "vuex";
import uiConfig from "../config/config";

export default {
  data() {
    return {
      instruction_video_url: "",
    };
  },
  beforeMount() {
    const conf = uiConfig.uiConfig;
    this.instruction_video_url = conf.instruction_video_url;
  },
  methods: {
    ...mapActions(["updateClickAnalytics"]),
    validateForm() {
      return true;
    },
  },
};
</script>


<style scoped>
.overview-container {
  margin: 2%;
}

.heading-overview {
  font-weight: bolder;
  font-size: 250%;
  text-align: center;
}
.notebox {
  border: solid black 1px;
  width: 90%;
  padding: 5px;
  margin-left: 1%;
}
body {
  font-family: 'Open Sans', 'sans-serif';
  width: 100%;
  /* font-family: 'Montserrat', Arial, Helvetica, sans-serif; */
}
.bg-topbar {
  background-color: rgb(250, 240, 226);
}
.div {
  border: solid black 1px;
}
</style>
