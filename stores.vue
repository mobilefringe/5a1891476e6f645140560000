<template>
  <div class="page_container"> <!-- for some reason if you do not put an outer container div this component template will not render -->
  <div class="store-list-left-block">
        <div class="store-list-container">
        <div class="level-div hidden-phone">
            <p>LEVEL  </p>
            <p class="level_num" id="level_1" style="color:white;background:#aea99e">1</p>
            <p class="level_num" id="level_2">2</p>
        </div>
        <p class="directory_title">directory</p>
        <div class="dropdown_container hidden-phone">
            <p>SORT BY CATEGORY</p>
            <div class="category-DD-div">
                <v-select v-model="selected_cat" :options="allCatergories"></v-select>
                <!--<select onchange="javascript:load_cats(this.value)">-->
                <!--    <option value="all" selected>All</option>-->
                    
                <!--        <option value="Accessories / Handbags / Luggage  "><p>Accessories / Handbags / Luggage  </p></option>    -->
                    
                <!--        <option value="All Stores"><p>All Stores</p></option>    -->
                    
                <!--        <option value="Beauty / Spas / Salons / Health"><p>Beauty / Spas / Salons / Health</p></option>    -->
                    
                <!--        <option value="Bridal"><p>Bridal</p></option>    -->
                    
                <!--        <option value="Department Stores"><p>Department Stores</p></option>    -->
                    
                <!--        <option value="Electronics / Home / Specialty Stores   "><p>Electronics / Home / Specialty Stores   </p></option>    -->
                    
                <!--        <option value="Entertainment "><p>Entertainment </p></option>    -->
                    
                <!--        <option value="Infants / Children's"><p>Infants / Children's</p></option>    -->
                    
                <!--        <option value="Jewelry / Watches  "><p>Jewelry / Watches  </p></option>    -->
                    
                <!--        <option value="Men's  "><p>Men's  </p></option>    -->
                    
                <!--        <option value="NorthPark Cafés"><p>NorthPark Cafés</p></option>    -->
                    
                <!--        <option value="NorthPark Services"><p>NorthPark Services</p></option>    -->
                    
                <!--        <option value="Optical"><p>Optical</p></option>    -->
                    
                <!--        <option value="Restaurants / Beverages"><p>Restaurants / Beverages</p></option>    -->
                    
                <!--        <option value="Retailer Services"><p>Retailer Services</p></option>    -->
                    
                <!--        <option value="Shoes  "><p>Shoes  </p></option>    -->
                    
                <!--        <option value="Specialty Foods"><p>Specialty Foods</p></option>    -->
                    
                <!--        <option value="The Luxury Collection"><p>The Luxury Collection</p></option>    -->
                    
                <!--        <option value="Tweens / Teens"><p>Tweens / Teens</p></option>    -->
                    
                <!--        <option value="Women's"><p>Women's</p></option>    -->
                         
                <!--</select>-->
            </div>
        </div>
        <div class="alphabet-dd visible-phone">
        
            <!--<select onchange="javascript:load_cats(this.value)">-->
            <!--    <option value="" disabled selected>Select Category</option>-->
                
            <!--        <option value="Accessories / Handbags / Luggage  "><p>Accessories / Handbags / Luggage  </p></option>    -->
                
            <!--        <option value="All Stores"><p>All Stores</p></option>    -->
                
            <!--        <option value="Beauty / Spas / Salons / Health"><p>Beauty / Spas / Salons / Health</p></option>    -->
                
            <!--        <option value="Bridal"><p>Bridal</p></option>    -->
                
            <!--        <option value="Department Stores"><p>Department Stores</p></option>    -->
                
            <!--        <option value="Electronics / Home / Specialty Stores   "><p>Electronics / Home / Specialty Stores   </p></option>    -->
                
            <!--        <option value="Entertainment "><p>Entertainment </p></option>    -->
                
            <!--        <option value="Infants / Children's"><p>Infants / Children's</p></option>    -->
                
            <!--        <option value="Jewelry / Watches  "><p>Jewelry / Watches  </p></option>    -->
                
            <!--        <option value="Men's  "><p>Men's  </p></option>    -->
                
            <!--        <option value="NorthPark Cafés"><p>NorthPark Cafés</p></option>    -->
                
            <!--        <option value="NorthPark Services"><p>NorthPark Services</p></option>    -->
                
            <!--        <option value="Optical"><p>Optical</p></option>    -->
                
            <!--        <option value="Restaurants / Beverages"><p>Restaurants / Beverages</p></option>    -->
                
            <!--        <option value="Retailer Services"><p>Retailer Services</p></option>    -->
                
            <!--        <option value="Shoes  "><p>Shoes  </p></option>    -->
                
            <!--        <option value="Specialty Foods"><p>Specialty Foods</p></option>    -->
                
            <!--        <option value="The Luxury Collection"><p>The Luxury Collection</p></option>    -->
                
            <!--        <option value="Tweens / Teens"><p>Tweens / Teens</p></option>    -->
                
            <!--        <option value="Women's"><p>Women's</p></option>    -->
                     
            <!--</select>    -->
        </div>
        
        <div class="alphabet-dd visible-phone">
            <!--<select onchange="window.location.href='#'+this.value">-->
            <!--    <option value="" disabled selected>Select Store A-Z</option>-->
            <!--    <option value="A">A</option>-->
            <!--    <option value="B">B</option>-->
            <!--    <option value="C">C</option>-->
            <!--    <option value="D">D</option>-->
            <!--    <option value="E">E</option>-->
            <!--    <option value="F">F</option>-->
            <!--    <option value="G">G</option>-->
            <!--    <option value="H">H</option>-->
            <!--    <option value="I">I</option>-->
            <!--    <option value="J">J</option>-->
            <!--    <option value="K">K</option>-->
            <!--    <option value="L">L</option>-->
            <!--    <option value="M">M</option>-->
            <!--    <option value="N">N</option>-->
            <!--    <option value="O">O</option>-->
            <!--    <option value="P">P</option>-->
            <!--    <option value="Q">Q</option>-->
            <!--    <option value="R">R</option>-->
            <!--    <option value="S">S</option>-->
            <!--    <option value="T">T</option>-->
            <!--    <option value="U">U</option>-->
            <!--    <option value="V">V</option>-->
            <!--    <option value="W">W</option>-->
            <!--    <option value="X">X</option>-->
            <!--    <option value="Y">Y</option>-->
            <!--    <option value="Z">Z</option>-->
            <!--</select>-->
        </div>
        <div class="mobile_download_dd visible-phone">
            <div class="dropdown">
              <button class="btn btn-default dropdown-toggle mobile_download_btn" type="button" id="dropdownMenu1" data-toggle="dropdown" aria-haspopup="true" aria-expanded="true">
                Download Directories & Maps
              </button>
              <ul class="dropdown-menu ul_dropdown" aria-labelledby="dropdownMenu1">
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                        
                            <li><a href="https://www.mallmaverick.com/system/site_images/photos/000/031/625/original/NorthPark_Center_Map_AUG17.pdf?1502307376" download="NorthPark Center Map August 2017" target="_blank" >NorthPark Center Map August 2017</a></li>
                        
                            <li><a href="https://www.mallmaverick.com/system/site_images/photos/000/003/967/original/WalkingMap_8-14_Online_Final.pdf?1446671651" download="Walking Map" target="_blank" >Walking Map</a></li>
                        
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
                    
                
              </ul>
            </div>
        </div>
          
        
            <ul class="store-listing">
            <a class="hidden-anchor" id="#"></a>
                        <li class="directory_header">#</li>
                        
                        <li>
                        <a href="/stores/northpark-7-for-all-mankind"><p class="directory_store_name">7 For All Mankind</p></a>
                        
                         
                        <a href="tel:214.346.5914" class="visible-phone"><img class="mobile-store-phone-icon" src="https://www.mallmaverick.com/system/site_images/photos/000/005/019/original/icon_call.png?1412199299"/></a>
                        </li>
                        </ul>
        </div>
    </div>
    <div class="store-list-map-block">
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
                  selected_cat : null
                }
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
                allCatergories() {
                    return this.$store.getters.processedCategories;
                }
            }
        });
        Vue.component('v-select', VueSelect.VueSelect);
    });
</script>
