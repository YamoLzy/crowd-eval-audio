<!--
    The sliders on this page were developed based on this superb CodePen by Ana Tudor - https://codepen.io/thebabydino/pen/NWWerZG 
-->
<template>
  <div class="row animatedsound-container" :id="id">
    <div id="errorModal" class="modal">
      <div class="modal-content">
        <p>
          Please listen to <span style="font-weight: bolder">all</span> sound
          clips and both the
          <span style="font-weight: bolder">arrangements fully</span> and
          adjust/move/re-position
          <span style="font-weight: bolder">all the sliders</span> for each
          audio clip accordingly before going to the next screen.
        </p>
        <span><button @click="closeModal">ok!</button></span>
      </div>
    </div>

    <div id="oneAudioOnlyModal" class="modal">
      <div class="modal-content">
        <p>Please listen very closely to <b>one audio clip</b> at a time.</p>
        <span><button @click="closeModal">ok!</button></span>
      </div>
    </div>

    <div class="heading row">
      <div class="col-3">&nbsp;</div>
      <div class="col-7 text-center">3.{{task_index+1}} Audio Perceptual Ordering Task</div>
      <div class="col-2">&nbsp;</div>
    </div>
    <div>&nbsp;</div>

    <div class="row">
      Please follow the instructions for each step below to complete this task.
    </div>
    <div>&nbsp;</div>
    <div class="row">
      The aim of this task is to position few audio samples between 2 reference
      samples, in a certain order (based on how your hear/perceive the sounds).
    </div>

    <div>&nbsp;</div>

    <div id="all-inputs" class="invisible" style="max-height: 10px">
      <!-- <div id="all-inputs"> -->
      <div id="ref-1-surrounding" class="dotted-border">
        <div
          style="
            --colorbg: grey;
            padding: 5px;
            border: solid black 1px;
            background-color: var(--colorbg);
          "
        >
          <audio
            id="ref_1_audio"
            controls
            controlsList="nodownload noplaybackrate"
            @ended="
              listenedCheck('ref_1_listened');
              removeSpotlight($event, 'ref-1-surrounding');
            "
            @play="
              playCheck($event);
              addSpotlight('ref-1-surrounding', 'ref_1_value');
            "
            @pause="removeSpotlight($event, 'ref-1-surrounding', 'ref_1_value')"
          >
            <source :src="ref1_url" type="audio/wav" />
          </audio>
        </div>
      </div>
      <div>&nbsp;</div>
      <div id="clip-1-surrounding" class="dotted-border">
        <div
          style="
            --colorbg: #cd2026;
            padding: 5px;
            border: solid black 1px;
            background-color: var(--colorbg);
          "
        >
          <audio
            id="clip_1_audio"
            controls
            controlsList="nodownload noplaybackrate"
            @ended="
              listenedCheck('clip_1_listened');
              removeSpotlight($event, 'clip-1-surrounding', 'clip_1_value');
            "
            @play="
              playCheck($event);
              addSpotlight('clip-1-surrounding', 'clip_1_value');
            "
            @pause="
              removeSpotlight($event, 'clip-1-surrounding', 'clip_1_value')
            "
          >
            <source :src="audio_1_url" type="audio/wav" />
          </audio>
        </div>
      </div>

      <div>&nbsp;</div>
      <div id="clip-2-surrounding" class="dotted-border">
        <div
          style="
            --colorbg: #4aa564;
            padding: 5px;
            border: solid black 1px;
            background-color: var(--colorbg);
          "
        >
          <audio
            id="clip_2_audio"
            controls
            controlsList="nodownload noplaybackrate"
            @ended="
              listenedCheck('clip_2_listened');
              removeSpotlight($event, 'clip-2-surrounding', 'clip_2_value');
            "
            @play="
              playCheck($event);
              addSpotlight('clip-2-surrounding', 'clip_2_value');
            "
            @pause="
              removeSpotlight($event, 'clip-2-surrounding', 'clip_2_value')
            "
          >
            <source :src="audio_2_url" type="audio/wav" />
          </audio>
        </div>
      </div>

      <div>&nbsp;</div>
      <div id="clip-3-surrounding" class="dotted-border">
        <div
          style="
            --colorbg: #f9c642;
            padding: 5px;
            border: solid black 1px;
            background-color: var(--colorbg);
          "
        >
          <audio
            id="clip_3_audio"
            controls
            controlsList="nodownload noplaybackrate"
            @ended="
              listenedCheck('clip_3_listened');
              removeSpotlight($event, 'clip-3-surrounding', 'clip_3_value');
            "
            @play="
              playCheck($event);
              addSpotlight('clip-3-surrounding', 'clip_3_value');
            "
            @pause="
              removeSpotlight($event, 'clip-3-surrounding', 'clip_3_value')
            "
          >
            <source :src="audio_3_url" type="audio/wav" />
          </audio>
        </div>
      </div>

      <div>&nbsp;</div>
      <div id="clip-4-surrounding" class="dotted-border">
        <div
          style="
            --colorbg: #0071bc;
            padding: 5px;
            border: solid black 1px;
            background-color: var(--colorbg);
          "
        >
          <audio
            id="clip_4_audio"
            controls
            controlsList="nodownload noplaybackrate"
            @ended="
              listenedCheck('clip_4_listened');
              removeSpotlight($event, 'clip-4-surrounding', 'clip_4_value');
            "
            @play="
              playCheck($event);
              addSpotlight('clip-4-surrounding', 'clip_4_value');
            "
            @pause="
              removeSpotlight($event, 'clip-4-surrounding', 'clip_4_value')
            "
          >
            <source :src="audio_4_url" type="audio/wav" />
          </audio>
        </div>
      </div>

      <div>&nbsp;</div>
      <div id="clip-5-surrounding" class="dotted-border">
        <div
          style="
            --colorbg: darkorange;
            padding: 5px;
            border: solid black 1px;
            background-color: var(--colorbg);
          "
        >
          <audio
            id="clip_5_audio"
            controls
            controlsList="nodownload noplaybackrate"
            @ended="
              listenedCheck('clip_5_listened');
              removeSpotlight($event, 'clip-5-surrounding', 'clip_5_value');
            "
            @play="
              playCheck($event);
              addSpotlight('clip-5-surrounding', 'clip_5_value');
            "
            @pause="
              removeSpotlight($event, 'clip-5-surrounding', 'clip_5_value')
            "
          >
            <source :src="audio_5_url" type="audio/wav" />
          </audio>
        </div>
      </div>

      <div>&nbsp;</div>

      <div id="ref-2-surrounding" class="dotted-border">
        <div
          style="
            --colorbg: grey;
            padding: 5px;
            border: solid black 1px;
            background-color: var(--colorbg);
          "
        >
          <audio
            id="ref_2_audio"
            controls
            controlsList="nodownload noplaybackrate"
            @ended="
              listenedCheck('ref_2_listened');
              removeSpotlight($event, 'ref-2-surrounding');
            "
            @play="
              playCheck($event);
              addSpotlight('ref-2-surrounding', 'ref_2_value');
            "
            @pause="removeSpotlight($event, 'ref-2-surrounding', 'ref_2_value')"
          >
            <source :src="ref2_url" type="audio/wav" />
          </audio>
        </div>
      </div>
    </div>

    <div class="step-content row">
      <div>1.</div>
      <div>&nbsp;</div>
      <div>
        Hover your mouse over each of the colored thumbs below to listen to the
        audio samples.<br /><br />
        The thumbs in
        <span style="background-color: #3b3a39; color: white; padding: 2px"
          >black</span
        >
        are your reference audio samples.<br />
        Please arrange/position the remaining thumbs in
        <span style="background-color: #cd2026; color: black; padding: 2px"
          >red</span
        >,
        <span style="background-color: #4aa564; color: black; padding: 2px"
          >green</span
        >,
        <span style="background-color: #f9c642; color: black; padding: 2px"
          >yellow</span
        >,
        <span style="background-color: #0071bc; color: black; padding: 2px"
          >blue</span
        >,
        <span style="background-color: darkorange; color: black; padding: 2px"
          >orange</span
        >
        in between the two references in a certain perceptual order.
      </div>
    </div>

    <div id="samples-container">
      <div>&nbsp;</div>

      <div class="wrap" role="group">
        <input
          id="ref_1_value"
          name="ref_1_value"
          type="range"
          min="0"
          value="0"
          max="0"
          style="--thumbcolor: #3b3a39; --thumbborder: transparent"
          @mouseover="
            mouseoverPlay('ref_1_audio');
            updateClickAnalytics('task_ref_1_sound');
          "
          @mouseout="mouseoutPause('ref_1_audio')"
        />

        <input
          id="clip_1_value"
          name="clip_1_value"
          type="range"
          min="0"
          max="100"
          style="--thumbcolor: #cd2026; --thumbborder: transparent"
          @change="
            sliderChanged('clip_1_slider_changed', $event);
            updateClickAnalytics('task_clip_1_slider');
          "
          @mouseover="
            mouseoverPlay('clip_1_audio');
            updateClickAnalytics('task_clip_1_sound');
          "
          @mouseout="mouseoutPause('clip_1_audio')"
          v-model="formData[id+'_clip_1_value']"
        />
        <input
          id="clip_2_value"
          name="clip_2_value"
          type="range"
          min="0"
          max="100"
          style="--thumbcolor: #4aa564; --thumbborder: transparent"
          @change="
            sliderChanged('clip_2_slider_changed', $event);
            updateClickAnalytics('task_clip_2_slider');
          "
          @mouseover="
            mouseoverPlay('clip_2_audio');
            updateClickAnalytics('task_clip_2_sound');
          "
          @mouseout="mouseoutPause('clip_2_audio')"
          v-model="formData[id+'_clip_2_value']"
        />
        <input
          id="clip_3_value"
          name="clip_3_value"
          type="range"
          min="0"
          max="100"
          style="--thumbcolor: #f9c642; --thumbborder: transparent"
          @change="
            sliderChanged('clip_3_slider_changed', $event);
            updateClickAnalytics('task_clip_3_slider');
          "
          @mouseover="
            mouseoverPlay('clip_3_audio');
            updateClickAnalytics('task_clip_3_sound');
          "
          @mouseout="mouseoutPause('clip_3_audio')"
          v-model="formData[id+'_clip_3_value']"
        />
        <input
          id="clip_4_value"
          name="clip_4_value"
          type="range"
          min="0"
          max="100"
          style="--thumbcolor: #0071bc; --thumbborder: transparent"
          @change="
            sliderChanged('clip_4_slider_changed', $event);
            updateClickAnalytics('task_clip_4_slider');
          "
          @mouseover="
            mouseoverPlay('clip_4_audio');
            updateClickAnalytics('task_clip_4_sound');
          "
          @mouseout="mouseoutPause('clip_4_audio')"
          v-model="formData[id+'_clip_4_value']"
        />
        <input
          id="clip_5_value"
          name="clip_5_value"
          type="range"
          min="0"
          max="100"
          style="--thumbcolor: darkorange; --thumbborder: transparent"
          @change="
            sliderChanged('clip_5_slider_changed', $event);
            updateClickAnalytics('task_clip_5_slider');
          "
          @mouseover="
            mouseoverPlay('clip_5_audio');
            updateClickAnalytics('task_clip_5_sound');
          "
          @mouseout="mouseoutPause('clip_5_audio')"
          v-model="formData[id+'_clip_5_value']"
        />
        <input
          id="ref_2_value"
          name="ref_2_value"
          type="range"
          min="99"
          value="100"
          max="100"
          style="--thumbcolor: #3b3a39; --thumbborder: transparent"
          @mouseover="
            mouseoverPlay('ref_2_audio');
            updateClickAnalytics('task_ref_2_sound');
          "
          @mouseout="mouseoutPause('ref_2_audio')"
        />
      </div>
    </div>

    <div id="relative-lines-section-container">
      <div>&nbsp;</div>
      <div id="relative-lines-section">
        <div>&nbsp;</div>
        <div class="relative-lines-section-1">&nbsp;</div>
        <div class="relative-lines-section-2">&nbsp;</div>
        <div>&nbsp;</div>
      </div>
      <div>&nbsp;</div>
    </div>

    <div class="step-content row">
      <div>2.</div>
      <div>&nbsp;</div>
      <div>
        <span style="font-weight: bold">Adjust Ordering Step</span>: Please
        click the button below to listen to your arrangement. <br />Does the
        arrangement sound to be in a certain order/seqeuence
        <span style="font-weight: bold; text-decoration: underline"
          >overall</span
        >? If not, please redo from Step 1.
      </div>
    </div>
    <div>&nbsp;</div>
    <div class="step-content row">
      <div>&nbsp;</div>
      <div>&nbsp;</div>
      <div>
        <button
          id="arrangementBtn_ordering"
          @click="
            listenArrangement($event, 'ordering_arrangement_listened');
            updateClickAnalytics('task_ordering_arrangement_button');
          "
        >
          Click Here To Listen to the Arrangement To Verify Ordering
        </button>
      </div>
    </div>
    <div>&nbsp;</div>
    <div class="step-content">
      <div>&nbsp;</div>
      <div>&nbsp;</div>
      <div>
        <input
          type="checkbox"
          id="ordering_checkbox"
          name="ordering_checkbox"
          value="ordered"
          @change="update_checkbox($event)"
          v-model="formData[id+'_ordering_checkbox']"
          disabled
        />
        <label for="ordering_checkbox">
          &nbsp;I have listened to the arrangement and verified that it is in
          the correct order of sequence.</label
        ><br />
      </div>
    </div>

    <div>&nbsp;</div>
    <div>&nbsp;</div>

    <div class="step-content row">
      <div>3.</div>
      <div>&nbsp;</div>
      <div>
        <span style="font-weight: bold">Adjust Relative Position Step</span>:
        Please click the button below to listen to your arrangement again.
        <br />Does the arrangement sound such that each clip is at a correct
        distance/spacing
        <span style="font-weight: bold; text-decoration: underline"
          >relative</span
        >
        to its neighbor? If not, please redo from Step 1.
      </div>
    </div>
    <div>&nbsp;</div>
    <div class="step-content row">
      <div>&nbsp;</div>
      <div>&nbsp;</div>
      <div>
        <button
          id="arrangementBtn_distance"
          @click="
            listenArrangement($event, 'distance_arrangement_listened');
            updateClickAnalytics('task_distance_arrangement_button');
          "
        >
          Click Here To Listen to the Arrangement To Verify Distance/Spacing
        </button>
      </div>
    </div>
    <div>&nbsp;</div>
    <div class="step-content">
      <div>&nbsp;</div>
      <div>&nbsp;</div>
      <div>
        <input
          type="checkbox"
          id="distance_checkbox"
          name="distance_checkbox"
          value="distance"
          @change="update_checkbox($event)"
          v-model="formData[id+'_distance_checkbox']"
          disabled
        />
        <label for="distance_checkbox">
          &nbsp;I have listened to the arrangement and verified that the
          distance/spacing of the samples is correct.</label
        ><br />
      </div>
    </div>

    <div>&nbsp;</div>
    <div>&nbsp;</div>
  </div>
</template>
<script  type="module">
import { mapActions, mapGetters } from "vuex";
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
  created() {
    if(!Object.keys(this.formData).some((key) => key.startsWith(this.id))){ 
      //Init clip positions if user has not moved them yet.
      var obj = {};
      obj['clip_1_value'] = '45';
      obj['clip_2_value'] = '47';
      obj['clip_3_value'] = '49';
      obj['clip_4_value'] = '51';
      obj['clip_5_value'] = '53';
      this.updateFormData(obj);
    }
  },
  mounted(){
    document.getElementById('relative-lines-section').style.visibility = 'hidden';
  },
  computed: {
    ...mapGetters(["formData", "config", "currentLevel"]),
    ref1_url: function () {
      return this.audio_samples.ref1_url;
    },
    ref2_url: function () {
      return this.audio_samples.ref2_url;
    },
    audio_1_url: function () {
      return this.audio_samples.audio_1_url;
    },
    audio_2_url: function () {
      return this.audio_samples.audio_2_url;
    },
    audio_3_url: function () {
      return this.audio_samples.audio_3_url;
    },
    audio_4_url: function () {
      return this.audio_samples.audio_4_url;
    },
    audio_5_url: function () {
      return this.audio_samples.audio_5_url;
    },
    
  },
  methods: {
    ...mapActions(["updateFormData", "updateClickAnalytics"]),
    getFormDataValue(nm) {
      return this.formData[this.id+'_'+nm]
    },
    sliderChanged(nm, e) {
      var obj = {};
      obj[nm] = true;
      this.updateFormData(obj);
    },
    listenedCheck(nm) {
      var obj = {};
      obj[nm] = true;
      this.updateFormData(obj);
    },
    update_checkbox(e) {
      var obj = {};
      obj[e.target.name] = e.target.checked;
      this.updateFormData(obj);
    },
    dblclicked(audio_id) {
      document.getElementById(audio_id).play();
    },
    mouseoverPlay(audio_id) {
      if (!this.disable_mouse_over_and_out)
        document.getElementById(audio_id).play();
    },
    mouseoutPause(audio_id) {
      if (!this.disable_mouse_over_and_out)
        document.getElementById(audio_id).pause();
    },
    playCheck(e) {
      var allAudios = document.getElementsByTagName("audio");
      for (var i = 0; i < allAudios.length; i++) {
        if (allAudios[i].paused == false && allAudios[i] != e.target) {
          e.target.pause();
          oneAudioOnlyModal.style.display = "block";
        }
      }
    },
    addSpotlight(contId, thumbId) {
      if (thumbId !== undefined)
        document
          .getElementById(thumbId)
          .style.setProperty("--thumbborder", "black");
      document.getElementById(contId).style.border = "dashed black 2px";
    },
    removeSpotlight(e, contId, thumbId) {
      e.target.currentTime = 0;
      if (thumbId !== undefined)
        document
          .getElementById(thumbId)
          .style.setProperty("--thumbborder", "transparent");
      document.getElementById(contId).style.border = "none";
    },
    closeModal() {
      if (oneAudioOnlyModal) oneAudioOnlyModal.style.display = "none";
      if (errorModal) errorModal.style.display = "none";
    },
    showRelPositionIndicator(){
      return (this.current_playing_arrangement.indexOf('distance') > -1);
    },
    updateRelativePositions(){
      if(this.showRelPositionIndicator()){
        this.sounds_in_sequence.forEach((sound, ind) => {
          const sound_id = sound.id.split('_').slice(0,2).join('_');
          const sound_val = document.getElementById(sound_id+'_value').value

          if(sound_id.indexOf('ref')==-1){
            const prev_sound_id = this.sounds_in_sequence[ind-1].id.split('_').slice(0,2).join('_');
            const prev_sound_val = document.getElementById(prev_sound_id+'_value').value
            const rem_left_val = prev_sound_val;

            const next_sound_id = this.sounds_in_sequence[ind+1].id.split('_').slice(0,2).join('_');
            const next_sound_val = document.getElementById(next_sound_id+'_value').value
            const rem_right_val = 100 - next_sound_val;

            const left_width = (sound_val - prev_sound_val);
            const right_width = (next_sound_val - sound_val);

            this.left_rel_line_widths[sound_id] = left_width;
            this.right_rel_line_widths[sound_id] = right_width;
            this.rem_left_line_widths[sound_id] = rem_left_val;
            this.rem_right_line_widths[sound_id] = rem_right_val;
          }
        });
      }
    },
    playSequence() {
      if (this.sound_index == this.sounds_in_sequence.length) {
        arrangementBtn_distance.removeAttribute("disabled");
        arrangementBtn_ordering.removeAttribute("disabled");
        if (this.current_playing_arrangement.includes("ordering"))
          ordering_checkbox.removeAttribute("disabled");
        if (this.current_playing_arrangement.includes("distance"))
          distance_checkbox.removeAttribute("disabled");
        this.disable_mouse_over_and_out = false;
        return;
      }
      this.sounds_in_sequence[this.sound_index].addEventListener(
        "ended",
        this.playSequence
      );
      if (this.sound_index != 0)
        this.sounds_in_sequence[this.sound_index - 1].removeEventListener(
          "ended",
          this.playSequence
        );
      
      if(this.showRelPositionIndicator()){
        const slider_id = this.sounds_in_sequence[this.sound_index].id.split('_').slice(0,2).join('_') ;
        const sliderThumbColor = document.getElementById(slider_id+"_value").style.getPropertyValue("--thumbcolor");
        if(slider_id.indexOf('ref') == -1){
          document.getElementById('relative-lines-section').style.visibility = 'visible';
          document.getElementById('relative-lines-section').style.setProperty('--leftrelcolor',sliderThumbColor)
          document.getElementById('relative-lines-section').style.setProperty('--rightrelcolor',sliderThumbColor)
          document.getElementById('relative-lines-section').style.setProperty('--leftlinewidth',this.left_rel_line_widths[slider_id]+'%')
          document.getElementById('relative-lines-section').style.setProperty('--rightlinewidth',this.right_rel_line_widths[slider_id]+'%')
          document.getElementById('relative-lines-section').style.setProperty('--remleftlinewidth',this.rem_left_line_widths[slider_id]+'%')
          document.getElementById('relative-lines-section').style.setProperty('--remrightlinewidth',this.rem_right_line_widths[slider_id]+'%')
        } else {
          document.getElementById('relative-lines-section').style.visibility = 'hidden';
        }
      }
      
      this.sounds_in_sequence[this.sound_index].play();
      this.sound_index++;
    },
    listenArrangement(e, nm) {
      this.disable_mouse_over_and_out = true; // When arrangement is playing - nobody disturb it.

      arrangementBtn_distance.disabled = true;
      arrangementBtn_ordering.disabled = true;
      this.sounds_in_sequence = [];
      this.sound_index = 0;
      let arrangement = {
        ref_1: -1,
        clip_1: parseInt(document.getElementById("clip_1_value").value),
        clip_2: parseInt(document.getElementById("clip_2_value").value),
        clip_3: parseInt(document.getElementById("clip_3_value").value),
        clip_4: parseInt(document.getElementById("clip_4_value").value),
        clip_5: parseInt(document.getElementById("clip_5_value").value),
        ref_2: 10000,
      };

      arrangement = Object.entries(arrangement)
        .sort(([, a], [, b]) => a - b)
        .reduce((r, [k, v]) => ({ ...r, [k]: v }), {});

      let ind = 0;
      for (const key in arrangement) {
        this.sounds_in_sequence[ind] = document.getElementById(key + "_audio");
        ind++;
      }

      this.current_playing_arrangement = nm;

      this.updateRelativePositions();
      this.listenedCheck(nm);
      this.playSequence();
    },
    validateForm() {
      const ref_1_listened = this.getFormDataValue('ref_1_listened');
      const ref_2_listened = this.getFormDataValue('ref_2_listened');
      const clip_1_listened = this.getFormDataValue('clip_1_listened');
      const clip_2_listened = this.getFormDataValue('clip_2_listened');
      const clip_3_listened = this.getFormDataValue('clip_3_listened');
      const clip_4_listened = this.getFormDataValue('clip_4_listened');
      const clip_5_listened = this.getFormDataValue('clip_5_listened');
      const full_arrangement_listened =
        this.getFormDataValue('ordering_arrangement_listened') &&
        this.getFormDataValue('distance_arrangement_listened');

      const listened =
        ref_1_listened &&
        ref_2_listened &&
        clip_1_listened &&
        clip_2_listened &&
        clip_3_listened &&
        clip_4_listened &&
        clip_5_listened &&
        full_arrangement_listened;

      const clip_1_slider_changed = this.getFormDataValue('clip_1_slider_changed');
      const clip_2_slider_changed = this.getFormDataValue('clip_2_slider_changed');
      const clip_3_slider_changed = this.getFormDataValue('clip_3_slider_changed');
      const clip_4_slider_changed = this.getFormDataValue('clip_4_slider_changed');
      const clip_5_slider_changed = this.getFormDataValue('clip_5_slider_changed');

      const sliderChangedTest =
        clip_1_slider_changed &&
        clip_2_slider_changed &&
        clip_3_slider_changed &&
        clip_4_slider_changed &&
        clip_5_slider_changed;

      const allFieldsUpdated =
        this.getFormDataValue('distance_checkbox') &&
        this.getFormDataValue('distance_checkbox') &&
        this.getFormDataValue('ordering_checkbox') &&
        this.getFormDataValue('ordering_checkbox');

      if (!(listened && sliderChangedTest && allFieldsUpdated))
        errorModal.style.display = "block";
      return listened && sliderChangedTest && allFieldsUpdated;
      return true;
    },
  },
};
</script>

<style scoped>
/* fix too small font-size in both Chrome & Firefox */
* {
  font: inherit;
}

audio {
  width: 100%;
}

.animatedsound-container {
  margin-left: 1%;
}

.heading {
  width: 100%;
  font-weight: bold;
  font-size: 250%;
}

.notebox {
  border: solid black 1px;
  width: 90%;
  padding: 5px;
}

.step-content {
  display: grid;
  grid-template-columns: 2% 1% 95%;
  margin-left: 1%;
}

#all-refs {
  display: grid;
  grid-template-columns: 20% 60% 20%;
  width: 100%;
  padding-top: 1%;
  padding-left: 5%;
}

#all-inputs {
  display: grid;
  grid-template-columns: repeat(auto-fill, 13% 1%);
  width: 100%;
}

#relative-lines-section-container{
  display: grid;
  grid-template-columns: 3% 78% 17%;
  padding-left: 3%;
}

#relative-lines-section{
  display: grid;
  /* grid-template-columns: 25% 25% 25% 25%; */
  grid-template-columns: var(--remleftlinewidth) var(--leftlinewidth) var(--rightlinewidth) var(--remrightlinewidth);
  width: 100%;
  max-height: 5px;
}

.relative-lines-section-1{
  max-height: 0px;
  border: solid var(--leftrelcolor) 2px;
}

.relative-lines-section-2{
  max-height: 0px;
  border: solid var(--rightrelcolor) 2px;
}

#samples-container {
  display: grid;
  grid-template-columns: 2% 80%;
  width: 100%;
  padding-left: 3%;
}

.wrap {
  display: grid;
  grid-template: repeat(2, -webkit-max-content) 4em/1fr 1fr;
  grid-template: repeat(2, max-content) 4em/1fr 1fr;
  overflow: hidden;
  position: relative;
  margin: 0.3em auto;
  width: 100%;
  background-color: rgb(196, 196, 196);
}

input[type="range"] {
  grid-column: 1 / span v-bind(num_thumbs);
  grid-row: 3;
  z-index: 1;
  top: 0;
  left: 0;
  margin: 0;
  background: none;
  /* get rid of white Chrome background */
  --col: #000;
  pointer-events: none;
}

input[type="range"]::-webkit-slider-runnable-track,
input[type="range"]::-webkit-slider-thumb,
input[type="range"] {
  -webkit-appearance: none;
}

input[type="range"]::-webkit-slider-runnable-track {
  padding-bottom: 5em;
  width: 100%;
  height: 100%;
  background: none;
}

input[type="range"]::-moz-range-track {
  padding-bottom: 5em;
  width: 100%;
  height: 100%;
  background: none;
}

input[type="range"]::-webkit-slider-thumb {
  border: none;
  /* get rid of Firefox thumb border */
  width: 2.3em;
  height: 5em;
  border-radius: 0;
  /* get rid of Firefox corner rounding */
  background: linear-gradient(90deg, #fff 2px, transparent 0) calc(1.2em - 1px),
    radial-gradient(circle, var(--thumbcolor) calc(1em - 1px), transparent 1em),
    radial-gradient(
      circle,
      transparent 0.7em,
      var(--thumbborder) 0.7em 1.1em,
      transparent 1.2em
    );
  pointer-events: auto;
}

input[type="range"]::-moz-range-thumb {
  border: none;
  /* get rid of Firefox thumb border */
  width: 2.3em;
  height: 5em;
  border-radius: 0;
  /* get rid of Firefox corner rounding */
  background: linear-gradient(90deg, #fff 2px, transparent 0) calc(1.2em - 1px),
    radial-gradient(circle, var(--thumbcolor) calc(1em - 1px), transparent 1em),
    radial-gradient(
      circle,
      transparent 0.7em,
      var(--thumbborder) 0.7em 1.1em,
      transparent 1.2em
    );
  pointer-events: auto;
}

.range-active {
  border: solid black 1px;
}

input[type="range"]:focus {
  z-index: 2;
  outline: dotted 1px currentcolor;
}

/* The Modal (background) */
.modal {
  display: none;
  /* Hidden by default */
  position: fixed;
  /* Stay in place */
  z-index: 10;
  /* Sit on top */
  left: 0;
  top: 0;
  width: 100%;
  /* Full width */
  height: 100%;
  /* Full height */
  overflow: auto;
  /* Enable scroll if needed */
  background-color: rgb(0, 0, 0);
  /* Fallback color */
  background-color: rgba(0, 0, 0, 0.4);
  /* Black w/ opacity */
}

/* Modal Content/Box */
.modal-content {
  background-color: #fefefe;
  margin: 15% auto;
  /* 15% from the top and centered */
  padding: 20px;
  border: 1px solid #888;
  width: 33%;
  /* Could be more or less, depending on screen size */
}

/* The Close Button */
.close {
  color: #aaa;
  float: right;
  font-size: 28px;
  font-weight: bold;
}

.close:hover,
.close:focus {
  color: black;
  text-decoration: none;
  cursor: pointer;
}

#overlay-disabled {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  z-index: 10;
  visibility: hidden;
  background-color: rgba(0, 0, 0, 0.3);
}

.dotted-border {
  padding: 5px;
  border: dashed solid white 2px;
}
</style>
