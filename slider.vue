<template>
  <div class="container">
    <h3>Shopping Hours</h3>
    <p v-if="!hours.is_closed">{{todayDate | moment("ddd", timezone)}} {{hours.open_time | moment("LT", timezone)}} - {{hours.close_time | moment("LT", timezone)}}</p>
    <p v-if="hours.is_closed">Closed</p>
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

<style lang="scss" type="text/scss">
    .agile {
        position: relative;

        &, * {
            &:focus,
            &:active {
                outline: none;
            }
        }

        &__list {
            display: block;
            overflow: hidden;
            position: relative;
            width: 100%;
        }

        &__track {
            align-items: center;
            display: flex;
            justify-content: flex-start;

            .agile--disabled & {
                display: block;
            }
        }

        &__slide {
            display: block;

            .agile--fade & {
                opacity: 0;
                position: relative;
                z-index: 0;

                &--active {
                    opacity: 1;
                    z-index: 2;
                }

                &--expiring {
                    opacity: 1;
                    transition-duration: 0s;
                    z-index: 1;
                }
            }
        }

        &__arrow {
            &[disabled] {
                cursor: default;
            }
        }

        &__dots {
            align-items: center;
            display: flex;
            list-style: none;
            margin: 0;
            padding: 0;
            white-space: nowrap;
        }

        &__dot {
            button {
                cursor: pointer;
                display: block;
                font-size: 0;
                line-height: 0;
            }
        }
    }
</style>