<template>
  <div>
    <slot></slot>
  </div>
</template>

<script>
  define(["Vue", "moment", "moment-timezone", "vue-moment"], function(Vue, moment, tz, VueMoment) {
    return Vue.component("today-hours", {
      template: template, // the variable template will be injected,
      data: function() {
        return {
          todayDate: new Date(),
          description: "An example of integration of Mall Maverick with Vue.js"
        }
      },
      computed: {
        hours () {
          return this.$store.getters.getTodayHours;
        },
        timezone () {
          return this.$store.getters.getTimezone;
        }
      }
    });
  });
</script>
