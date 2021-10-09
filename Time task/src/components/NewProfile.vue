<template>
  <div>
    <ul class="">
      <li data-label="">{{ title }}</li>
      <li data-label="">{{ description }}</li>
      <li data-label="">{{ stertdate }}</li>
      <li data-label="">{{ enddate }}</li>
      <li data-label="">{{ assignedperson }}</li>
      <li>
        <the-time
          @save-time="savethetime"
          :index="index"
          :Totaltime="Totaltime"
        ></the-time>
      </li>
    </ul>
  </div>
</template>
<script>
import TheTime from "./TheTime.vue";
export default {
  components: {
    TheTime,
  },
  props: [
    "title",
    "description",
    "stertdate",
    "enddate",
    "assignedperson",
    "index",
    "Totaltime",
  ],
  data() {
    return {};
  },
  methods: {
    savethetime(ut, indtime) {
      this.$emit("update-event", ut, indtime);
    },
  },
};
</script>
<style scoped>
/* big */
@media screen and (min-width: 600px) {
  ul {
    display: table-row;
  }

  ul > li {
    display: table-cell;
    padding: 1em 2em;
    padding-left: 35px;
  }
}

/* small */
@media screen and (max-width: 599px) {
  ul {
    border: solid 1px #ccc;
    display: block;
    list-style: none;
    margin: 1em;
    padding: 0.5em 1em;
  }

  ul:first-child {
    display: none;
  }

  ul > li {
    display: block;
    padding: 0.25em 0;
  }

  ul:nth-child(odd) > li + li {
    border-top: solid 1px #ccc;
  }

  ul:nth-child(even) > li + li {
    border-top: solid 1px #eee;
  }

  ul > li:before {
    color: #000;
    content: attr(data-label);
    display: inline-block;
    font-size: 75%;
    font-weight: bold;
    text-transform: capitalize;
    vertical-align: top;
    width: 50%;
  }

  .list p {
    margin: -1em 0 0 50%;
  }
}

/* tiny */
@media screen and (max-width: 349px) {
  .list ul > li:before {
    display: block;
  }

  .list p {
    margin: 0;
  }
}
</style>

  <!-- <div>
    <h1>{{ title }}</h1>
    <p>{{ description }}</p>
    <p>{{ stertdate }}</p>
    <p>{{ enddate }}</p>
    <p>{{ assignedperson }}</p>
  </div> -->