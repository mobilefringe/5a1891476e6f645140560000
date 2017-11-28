<template>
    <div class="row page_container">
        <div class="banner_div">
            <div class="main_banner">
                <div  class="prev"></div>
                <slick ref="slick" :options="slickOptions">
                    <div class="" v-for="banner in banners">
                        <img :src="banner.image_url" class="" alt="">
                        <div class="banner_text" v-if="banner.description">
                            <p class="banner-description">{{banner.description}}</p>
                            <a :href="banner.url">
                                <div class="banner_see_more">  See All <i class="fa fa-chevron-right pull-right" aria-hidden="true"></i></div>
                            </a>
                        </div>
                    </div>
                </slick>
                <div class="next"></div>
            </div>
            
            <div class="top_two hidden-phone">
                <router-link v-for="feature in feature_items">
                    
                </router-link>
                <!--{% for item in site.feature_items_array %}-->
                <!--    {% if item.name == 'top_1' %}-->
                <!--        <a href='{{item.url}}' ><img class="top_image" src='{{item.feature_image_path}}'/></a>-->
                <!--    {% endif %}-->
                <!--    {% if item.name == 'top_2' %}-->
                <!--        <a href='{{item.url}}' ><img class="top_image" src='{{item.feature_image_path}}'/></a>-->
                <!--    {% endif %}-->
                <!--{% endfor %}-->
            </div>
        </div>
        
        <div style="border-top:4px double #aea99e">
            <div class="feature-div" style="height:580px">
                <span>
                    <!--{% for item in site.feature_items_array limit:3 %}-->
                    <!--    <div class="feature-box">-->
                    <!--        <p class="feature-title">{{item.name}}</p>-->
                    <!--        <img src="{{item.feature_image_path}}" class="feature-image" />-->
                    <!--        <p class="feature-html">{{item.html}}</p>-->
                    <!--        <p class="feature-desc">{{item.description | truncate: 100}}</p>-->
                    <!--        <span><a href="{{item.url}}" class="mobile_readmore" ><p class="feature-readmore">Read More</p><img src={{3573 | get_image_url}} class="pull-left"/></a></span>-->
                    <!--        {% if @can_edit == "true" %}-->
                    <!--            <a href="/feature_items/{{item.id}}/edit" class="btn btn-primary pull-right">Edit</a>-->
                    <!--        {% endif %} -->
                    <!--    </div>-->
                    <!--{% endfor %}-->
                </span>
            </div>
        </div>
    </div>
</template>

<script>
    define(["Vue", "vue!today_hours", "vue!search-component", 'vue!vue-slick'], function(Vue, TodayHoursComponent, SearchComponent, slick) {
        return Vue.component("home-component", {
            template: template, // the variable template will be injected
            data: function() {
                return {
                    title: "MM with Vue.js!",
                    description: "An example of integration of Mall Maverick with Vue.js",
                    suggestionAttribute: 'name',
                    search: '',
                    slickOptions: {
                        slidesToShow: 1,
                        dots : true,
                        arrows:true,
                        prevArrow: '.prev',
                        nextArrow: '.next',
                        autoplay: true
                        // Any other options that can be got from plugin documentation
                    }
                }
            },
            computed: {
                property(){
                  return this.$store.getters.getProperty;
                },
                processedStores() {
                  return this.$store.getters.processedStores;
                },
                banners () {
                    console.log(_.orderBy(this.$store.state.results.banners, ['position'], ['asc']));
                    return _.orderBy(this.$store.state.results.banners, ['position'], ['asc']);
                }
                feature_items () {
                    console.log(this.$store.state.results.feature_items);
                    return this.$store.state.results.feature_items;
                }
            },
            methods: {
                onOptionSelect(option) {
                  console.log('Selected option:', option)
                }
            }
        })
    })
</script>