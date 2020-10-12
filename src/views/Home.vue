<template>
  <div class="home">
    <Topic />
    <b-container class="bv-example-row">
      <b-row>
        <b-col sm="6" offset="3">
          <Trials
            v-if="Questions.length"
            :currentQuestion="Questions[index]"
            :next="next"
          />
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
// @ is an alias to /src
import Topic from "@/components/Topic.vue";
import Trials from "@/components/Trials.vue";
export default {
  name: "Home",
  components: {
    Topic,
    Trials
  },
  data() {
    return {
      Questions: [],
      index: 0
    };
  },
  methods: {
    next: function() {
      this.index++;
    }
  },
  mounted: function() {
    fetch("https://opentdb.com/api.php?amount=10&category=18&type=multiple", {
      method: "get"
    })
      .then(Response => {
        return Response.json();
      })
      .then(JSON => {
        this.Questions = JSON.results;
      });
  }
};
</script>
