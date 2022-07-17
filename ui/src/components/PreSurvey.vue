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
    <title>pre-survey</title>
</head>

<body>
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

    <div class="container-fluid" style="width: 100%">
    
        <div class="row">&nbsp;</div>
        <div class="row">
            <div class="col-1">&nbsp;</div>
            <div class="col-10">
                <h4><b><u>5. Pre-Survey</u></b></h4>
            </div>
            <div class="col-1">&nbsp;</div>
        </div>   


        <div class="row">&nbsp;</div>
        <div class="row">
            <div class="col-1">&nbsp;</div>
            <div class="col-10">
                1. In your opinion, generally, what is the difference between morphs and mixes/cross-fades?
            </div>
            <div class="col-1">&nbsp;</div>
        </div>
        <div class="row">
            <div class="col-1">&nbsp;</div>
            <div class="col-10">
                <div class="mb-3">
                  <textarea 
                    class="form-control" 
                    name="answer_1"
                    id="pre_survey_answer_1" 
                    rows="3" 
                    @change="update_field($event, 'answer_1')"
                  >
                  </textarea>
                </div>
            </div>
            <div class="col-1">&nbsp;</div>
        </div>


        <div class="row">&nbsp;</div>
        <div class="row">
            <div class="col-1">&nbsp;</div>
            <div class="col-10">
                2. Have you used any computer software before to generate morphs? 
                If yes, kindly outline the types of sound morphs you generated and their application.
            </div>
            <div class="col-1">&nbsp;</div>
        </div>
        <div class="row">
            <div class="col-1">&nbsp;</div>
            <div class="col-10">
                <div class="mb-3">
                  <textarea 
                    class="form-control" 
                    name="answer_2"
                    id="pre_survey_answer_2" 
                    rows="3" 
                    @change="update_field($event, 'answer_2')"
                  >
                  </textarea>
                </div>
            </div>
            <div class="col-1">&nbsp;</div>
        </div>
    </div>
</body>
</html>
</template>

<script>
import { mapActions, mapGetters } from "vuex";
export default {
  data() {
    return {
    };
  },
  created() {},
  computed: {
    ...mapGetters(["formData"]),
  },
  methods: {
    ...mapActions(["updateFormData"]),
    update_field($event, nm) {
      var obj = {};
      obj[nm] = $event.target.value;
      this.updateFormData(obj);
    },
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
