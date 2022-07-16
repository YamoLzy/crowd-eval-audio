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
    <title>pre-test</title>
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

    <div class="container-fluid" style="width: 100%">
    
        <div class="row">&nbsp;</div>
        <div class="row">
            <div class="col-1">&nbsp;</div>
            <div class="col-10">
                <h4><b><u>3. Pre-Test</u></b></h4>
            </div>
            <div class="col-1">&nbsp;</div>
        </div>   
    
        <div class="row">&nbsp;</div>
        <div class="row">
            <div class="col-1">&nbsp;</div>
            <div class="col-10">
                On this page, you will have <b><u>10 sets of short interpolated audio samples.</u></b>
                Each set has two clean audio clips (reference A and reference B) and two samples.
                Please listen to each sample fully and answer if they are morphs or mixes/cross-fades.
            </div>
            <div class="col-1">&nbsp;</div>
        </div>  

        <div class="row">&nbsp;</div>
        <div class="row">&nbsp;</div>

        <div
          v-for="question_num in task_num_questions"
          :key="question_num"
          :value="question_num"
        >
          <div class="row">
            <div class="col-1">&nbsp;</div>
            <div class="col-2 text-center"><b>Reference A</b></div>
            <div class="col-2 text-center"><b>Reference B</b></div>
            <div class="col-2">&nbsp;</div>
            <div class="col-2 text-center"><b>Reference A</b></div>
            <div class="col-2 text-center"><b>Reference B</b></div>
            <div class="col-1">&nbsp;</div>
          </div>  
          <div class="row">
            <div class="col-1">&nbsp;</div>
            <div class="col-2 d-flex justify-content-center">
                <audio controls>
                    <source
                        :src="get_sample_url(question_num, 1, 'a')"
                        type="audio/wav"
                    />
                </audio>
            </div>
            <div class="col-2 d-flex justify-content-center">
                <audio controls>
                    <source
                        :src="get_sample_url(question_num, 2, 'b')"
                        type="audio/wav"
                    />
                </audio>
            </div>
            <div class="col-2">&nbsp;</div>
            <div class="col-2 d-flex justify-content-center">
                <audio controls>
                    <source
                        :src="get_sample_url(question_num, 1, 'a')"
                        type="audio/wav"
                    />
                </audio>
            </div>
            <div class="col-2 d-flex justify-content-center">
                <audio controls>
                    <source
                        :src="get_sample_url(question_num, 2, 'b')"
                        type="audio/wav"
                    />
                </audio>
            </div>
            <div class="col-1">&nbsp;</div>
          </div>
          <div class="row">&nbsp;</div>
          <div class="row">
            <div class="col-6 text-center"><b>Sample 1</b></div>
            <div class="col-6 text-center"><b>Sample 2</b></div>
          </div>  
          <div class="row">
            <div class="col-2">&nbsp;</div>
            <div class="col-2 d-flex justify-content-center">
                <audio controls>
                    <source
                        :src="get_sample_url(question_num, 1)"
                        type="audio/wav"
                    />
                </audio>
            </div>
            <div class="col-4">&nbsp;</div>
            <div class="col-2 d-flex justify-content-center">
                <audio controls>
                    <source
                        :src="get_sample_url(question_num, 2)"
                        type="audio/wav"
                    />
                </audio>
            </div>
            <div class="col-2">&nbsp;</div>
          </div>
          <div class="row">&nbsp;</div>
          <div class="row">
            <div class="col-1">&nbsp;</div>
            <div class="col-10">
                {{ question_num }}. Which audio sample is a morph and not a mix/crossfade? 
            </div>
            <div class="col-1">&nbsp;</div>
          </div>  
          <div class="row">&nbsp;</div>
          <div class="row">
            <div class="col-1">&nbsp;</div>
            <div class="col-10">
              <div class="form-check">
                <input
                  class="form-check-input"
                  type="radio"
                  :name="'question_num_' + question_num "
                  :id="'question_num_' + question_num + '_sample_1_selected'"
                  :value="'question_num_' + question_num + '_sample_1_selected'"
                  @change="update_checkbox($event)"
                />
                <label
                  class="form-check-label"
                  for="'question_num_'+question_num+'_sample_2'"
                >
                  Sample 1 is a morph.
                </label>
              </div>
              <div class="form-check">
                <input
                  class="form-check-input"
                  type="radio"
                  :name="'question_num_' + question_num"
                  :id="'question_num_' + question_num + '_sample_2_selected'"
                  :value="'question_num_' + question_num + '_sample_2_selected'"
                  @change="update_checkbox($event)"
                />
                <label
                  class="form-check-label"
                  for="'question_num_'+question_num+'_sample_2'"
                >
                  Sample 2 is a morph.
                </label>
              </div>
            </div>
            <div class="col-1">&nbsp;</div>
          </div>  
          <div class="row">&nbsp;</div>
          <div class="row">
            <div class="col-1">&nbsp;</div>
            <div class="col-10"><hr /></div>
            <div class="col-1">&nbsp;</div>
          </div>
        </div>
    </div>
</body>
</html>
</template>


<script type="module">
import { mapActions } from "vuex";
export default {
  props: ["id", "audio_samples", "task_index"],
  data() {
    return {
      task_num_questions: 0,
      task_audio_samples: [],
    };
  },
  created() {
    this.task_num_questions = this.audio_samples.num_questions;
    this.task_audio_samples = this.audio_samples;
    console.log(this.task_num_questions);
  },
  methods: {
    ...mapActions(["updateFormData", "updateClickAnalytics"]),
    update_checkbox(e) {
      var obj = {};
      obj[e.target.name] = e.target.value;
      this.updateFormData(obj);
    },
    get_sample_url(row, col, refname) {
      if (refname != "") {
        return this.task_audio_samples[
          "q_" + row + "_col_" + col + "_ref_" + refname
        ];
      } else {
        return this.task_audio_samples["q_" + row + "_col_" + col + "_sample"];
      }
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
audio { width: 220px; }
</style>
