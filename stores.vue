<template>
    <div class="page_container"> <!-- for some reason if you do not put an outer container div this component template will not render -->
        <div class="store-list-left-block col-md-4">
            <div class="store-list-container">
                <div class="dropdown_container hidden-phone">
                    <p>SORT BY CATEGORY</p>
                    <div class="category-DD-div">
                        <v-select v-model="selected_cat" :options="dropDownCats" class="open"></v-select>
                    </div>
                </div>
                <div class="alphabet-dd visible-phone">
                    <v-select v-model="selected_cat" :options="dropDownCats" class="open"></v-select>
                </div>
                
                <div class="alphabet-dd visible-phone">
                    <v-select v-model="selected_alpha" :options="alphabet" class="open"></v-select>
                </div>
          
                <ul class="store-listing">
                    <li v-for="store in allStores">
                        <a :href="'/stores/'+store.slug"><p class="directory_store_name">{{store.name}}</p></a>
                    </li>
                </ul>
            </div>
    </div>
    <div class="store-list-map-block col-md-8">
        <div class="main-map">
            <div id="mapsvg_store_detail"></div>
        </div>
        
        <p class="store-list-map-block-label">Downloadable directories & maps</p>
        <div class="download_dd_div">
            <select class="download_dd" id ="download_dd">
                 
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                        
                            <option value="https://www.mallmaverick.com/system/site_images/photos/000/031/625/original/NorthPark_Center_Map_AUG17.pdf?1502307376">NorthPark Center Map August 2017</option>
                        
                            <option value="https://www.mallmaverick.com/system/site_images/photos/000/003/967/original/WalkingMap_8-14_Online_Final.pdf?1446671651">Walking Map</option>
                        
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
            </select>
        </div>
       <p class="feature-readmore" onclick="javascript:download_pdf()">Download</p><img style="margin-right:10px" src=https://www.mallmaverick.com/system/site_images/photos/000/003/573/original/arrow-btn.gif?1408990113 class="pull-left"/>    
    </div>
    <!--<ul class="menu">-->
    <!--  <li><a v-on:click="changeMode('alphabetical')">Alphabetical</a></li>-->
    <!--  <li><a v-on:click="changeMode('category')">Category</a></li>-->
    <!--</ul>-->
    <!--<hr/>-->
    <!--<div class="columns large-12" v-for="(stores, index) in storesByAlphaIndex" v-if="listMode === 'alphabetical'">-->
    <!--  <div class="list_header">-->
    <!--    <b>{{index}}</b>-->
    <!--    <hr/>-->
    <!--  </div>-->
    <!--  <div class="store-section" v-for="store in stores">-->
    <!--    <router-link :to="{ name: 'storeDetails', params: { id: store.slug }}">{{store.name}}</router-link>-->
    <!--    <hr/>-->
    <!--  </div>-->
      <!-- <div class="card">
        <div class="card-divider">
          {{ store.name }}
        </div>
        <div class="card-section center">
          <a :href="store.image_url" target="_blank"><img :src="store.image_url"></a>
        </div>
        <div class="card-section">
          <div class="center">
            <router-link :to="{ name: 'storeDetails', params: { id: store.slug }}">View Details</router-link>
          </div>
        </div>
      </div> -->
    <!--</div>-->
    <!--<div class="columns large-12" v-for="(stores, index) in storesByCategoryName" v-if="listMode === 'category'">-->
    <!--  <div class="list_header">-->
    <!--    <b>{{index}}</b>-->
    <!--    <hr/>-->
    <!--  </div>-->
    <!--  <div class="store-section" v-for="store in stores">-->
    <!--    <router-link :to="{ name: 'storeDetails', params: { id: store.slug }}">{{store.name}}</router-link>-->
    <!--    <hr/>-->
    <!--  </div>-->
    <!--</div>-->
  </div>
</template>

<style>
  .center{
    text-align: center
  }
  .store-section a{
    color: #708090;
  }
</style>

<script>
    define(["Vue",'vue-select'], function(Vue, VueSelect) {
        return Vue.component("stores-component", {
            template: template, // the variable template will be injected
            data: function() {
                return {
                  listMode: "alphabetical",
                  selected_cat : null,
                  selected_alpha : null,
                  alphabet : ["A", "B", "C", "D", "E", "F", "G", "H", "I", "J", "K", "L", "M", "N", "O", "P", "Q", "R", "S", "T", "U", "V", "W", "X", "Y", "Z"],
                }
            },
            mounted() {
            },
            methods: {
                changeMode (mode) {
                  this.listMode = mode;
                }
            },
            computed: {
                storesByAlphaIndex() {
                    return this.$store.getters.storesByAlphaIndex;
                },
                storesByCategoryName() {
                    return this.$store.getters.storesByCategoryName;
                },
                allStores() {
                  return this.$store.getters.processedStores;
                },
                allCatergories() {
                    return this.$store.getters.processedCategories;
                },
                dropDownCats () {
                    return _.map(this.allCatergories, 'name');
                }
            }
        });
    });
</script>
