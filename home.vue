<template>
    <div class="row page_container">
        <div class="banner_div">
            <!--<div class="flexslider">-->
            <!--    <ul class="slides"> -->
            <!--        <li id="" style="display:none" v-for="banner in banners">-->
            <!--            <a :href="banner.url" class="flex-image">-->
            <!--                <img :src="banner.image_url" data-pin-no-hover="true"/>-->
            <!--            </a>-->
            <!--            <p class="banner-description">{{banner.description}}</p>-->
            <!--        </li>-->
            <!--    </ul>-->
            <!--</div>-->
            <!--<agile :arrows="false" :dots="true" :infinite="false">-->
            <!--    <div class="slide" v-for="banner in banners">-->
            <!--        <img :src="banner.image_url" class="" alt="">-->
            <!--        <div class="banner_text">-->
            <!--            <p class="banner-description">{{banner.description}}</p>-->
            <!--            <a :href="banner.url">-->
            <!--                <div class="banner_see_more">  See All <i class="fa fa-chevron-right pull-right" aria-hidden="true"></i></div>-->
            <!--            </a>-->
            <!--        </div>-->
                    
            <!--    </div>-->
            <!--</agile>-->
            
            <slick ref="slick" :options="slickOptions">
                <div class="" v-for="banner in banners">
                    <img :src="banner.image_url" class="" alt="">
                    <div class="banner_text">
                        <p class="banner-description">{{banner.description}}</p>
                        <a :href="banner.url">
                            <div class="banner_see_more">  See All <i class="fa fa-chevron-right pull-right" aria-hidden="true"></i></div>
                        </a>
                    </div>
                    
                </div>
            </slick>
            <div class="top_two hidden-phone">
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
    define(["Vue", "vue!today_hours", "vue!search-component", 'vue!vue-agile', 'vue!vue-slick'], function(Vue, TodayHoursComponent, SearchComponent, agile, slick) {
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
                        prevArrow: $('.prev'),
                        nextArrow: $('.next')
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
            },
            methods: {
                onOptionSelect(option) {
                  console.log('Selected option:', option)
                }
            }
        })
    })
</script>