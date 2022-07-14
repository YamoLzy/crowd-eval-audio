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
    <title>Individual-trials</title>
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
                <h4><b><u>5. Individual Listensing Trials</u></b></h4>
            </div>
            <div class="col-1">&nbsp;</div>
        </div>   
    
        <div class="row">&nbsp;</div>
        <div class="row">
            <div class="col-1">&nbsp;</div>
            <div class="col-10">
                On this page, you will be given <b><u>20 sets of interpolated audio samples.</u></b>
                Please listen to each sample fully and answer if they are morphs or mixes/cross-fades.
            </div>
            <div class="col-1">&nbsp;</div>
        </div>  
    

        <div class="row">&nbsp;</div>
        <div class="row">&nbsp;</div>
        <div class="row">
            <div class="col-1">&nbsp;</div>
            <div class="col-10"><hr></div>
            <div class="col-1">&nbsp;</div>
        </div>
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
            <div class="col-2">
                <audio controls>
                    <source src="audio/MixMorph/AlianComputer/8A.mp3" type="audio/wav">
                </audio>
            </div>
            <div class="col-2">
                <audio controls>
                    <source src="audio/MixMorph/AlianComputer/8B.mp3" type="audio/wav">
                </audio>
            </div>
            <div class="col-2">&nbsp;</div>
            <div class="col-2">
                <audio controls>
                    <source src="audio/MixMorph/AlianComputer/8A.mp3" type="audio/wav">
                </audio>
            </div>
            <div class="col-2">
                <audio controls>
                    <source src="audio/MixMorph/AlianComputer/8B.mp3" type="audio/wav">
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
            <div class="col-2">
                <audio controls>
                    <source src="audio/MixMorph/AlianComputer/8Morph.mp3" type="audio/wav">
                </audio>
            </div>
            <div class="col-4">&nbsp;</div>
            <div class="col-2">
                <audio controls>
                    <source src="audio/MixMorph/AlianComputer/8AB.Mix.5.mp3" type="audio/wav">
                </audio>
            </div>
            <div class="col-2">&nbsp;</div>
        </div>
        <div class="row">&nbsp;</div>
        <div class="row">
            <div class="col-1">&nbsp;</div>
            <div class="col-10">
                1. Which audio sample is a morph and not a mix/crossfade? 
            </div>
            <div class="col-1">&nbsp;</div>
        </div>  
        <div class="row">&nbsp;</div>
        <div class="row">
            <div class="col-1">&nbsp;</div>
            <div class="col-10">
                <div class="radio disabled" id="onequestion">
                    <label class="checkbox-inline">
                        <input type="radio" name="1" value="Morph" @change="update_checkbox($event)">Sample 1 is a morph.
                    </label>
                </div> <br>
                <div class="radio disabled" id="onequestion">
                    <label class="checkbox-inline">
                        <input type="radio" name="1" value="Mix" @change="update_checkbox($event)">Sample 2 is a morph.
                    </label>
                </div>
            </div>
            <div class="col-1">&nbsp;</div>
        </div>  
    </div>
</body>
</html>
</template>



<script type="module">
import { mapActions } from "vuex";
export default {
  props: ['id', 'audio_samples', 'task_index'],
  data() {
    return {
      num_thumbs: 7,
      sound_index: 0,
      sounds_in_sequence: [],
      current_playing_arrangement: "",
      disable_mouse_over_and_out: false,
      rem_left_line_widths: {},
      left_rel_line_widths: {},
      right_rel_line_widths: {},
      rem_right_line_widths: {},
    };
  },
  created() {},
  methods: {
    ...mapActions(["updateFormData", "updateClickAnalytics"]),
    update_checkbox(e) {
      var obj = {};
      obj[e.target.name] = e.target.checked;
      this.updateFormData(obj);
    },
    validateForm() {
      return true;
    },
  }
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
