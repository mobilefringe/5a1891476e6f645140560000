<style>
    .flexslider, .slides img{
        display:inline-block;
        width:708px;
        height:458px;
    }
    
    .flex-control-nav{
        bottom:5px;
        
    }
    
    .flex-control-paging li a{
        border-radius:50%;
        height:15px;
        width:15px;
    }
    
    
    
    .banner-description{
        display:none;
    }
    
    
    @media (max-width: 767px) {
        .flexslider, .slides img {
            display: inline-block;
            width: 100%;
            height:auto;
        }
        .flex-control-nav{
            right:0;
    }
</style>
<template>
    <div class="row page_container">
   



    <div class="banner_div">
    
        
        <div class="flexslider">
            <ul class="slides"> 
                {% assign counter = 1 %}
                {% for banner_image in banner_images %}
                    <li id="{{counter}}" style="display:none">
                        {% if banner_image.url != "" %}
                            <a href="{{banner_image.url}}" class="flex-image">
                                <img src="{{banner_image.image_url}}" data-pin-no-hover="true"/>
                              
                            </a>
                        {% else %}
                            <img src="{{banner_image.image_url}}" data-pin-no-hover="true" class="flex-image"/>
                           
                        {% endif %}
                        <p class="banner-description">{{banner_image.description}}</p>
                    {% assign counter = counter | plus:1 %}
                        
                    </li>
                {% endfor %}
            </ul>
        </div>
        
        
        <div class="top_two hidden-phone">
            {% for item in site.feature_items_array %}
                {% if item.name == 'top_1' %}
                    <a href='{{item.url}}' ><img class="top_image" src='{{item.feature_image_path}}'/></a>
                {% endif %}
                {% if item.name == 'top_2' %}
                    <a href='{{item.url}}' ><img class="top_image" src='{{item.feature_image_path}}'/></a>
                {% endif %}
            {% endfor %}
        </div>
    </div>
    
    <div style="border-top:4px double #aea99e">
        <div class="feature-div" style="height:580px">
            <span>
                {% for item in site.feature_items_array limit:3 %}
                    <div class="feature-box">
                        <p class="feature-title">{{item.name}}</p>
                        <img src="{{item.feature_image_path}}" class="feature-image" />
                        <p class="feature-html">{{item.html}}</p>
                        <p class="feature-desc">{{item.description | truncate: 100}}</p>
                        <span><a href="{{item.url}}" class="mobile_readmore" ><p class="feature-readmore">Read More</p><img src={{3573 | get_image_url}} class="pull-left"/></a></span>
                        {% if @can_edit == "true" %}
                            <a href="/feature_items/{{item.id}}/edit" class="btn btn-primary pull-right">Edit</a>
                        {% endif %} 
                    </div>
                {% endfor %}
            </span>
        </div>
    </div>
<script>
    $("#home_link").css("color","black");
    $(".feature-box:nth-child(-n+2)").css("margin-right","45px");
    $(document).ready(function() {
        $('.flexslider').flexslider({
            animation: "slide",
            controlNav: true,
            directionNav: true,        
            prevText: "Previous",
            nextText: "Next",
            start: function(){
                 $('.slides li').css("display","block"); 
            },
        });
      
    });
    
    $(".swipe_test").on("swipe",function(){
      alert("success");
    });
    
    $( ".slides li" ).hover(
      function() {
        $(this.id+"-pin").show();
      }, function() {
        $(this.id+"-pin").hide();
      }
    );
    
</script>

  </div>
</template>

<script>
  define(["Vue", "vue!today_hours", "vue!search-component"], function(Vue, TodayHoursComponent, SearchComponent) {
    return Vue.component("home-component", {
      template: template, // the variable template will be injected
      data: function() {
        return {
          title: "MM with Vue.js!",
          description: "An example of integration of Mall Maverick with Vue.js",
          suggestionAttribute: 'name',
          search: ''
        }
      },
      computed: {
        property(){
          return this.$store.getters.getProperty;
        },
        processedStores() {
          return this.$store.getters.processedStores;
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
