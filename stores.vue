<template>
    <div class="page_container"> <!-- for some reason if you do not put an outer container div this component template will not render -->
        <div class="store-list-left-block col-md-4 padding_top_20">
            <div class="store-list-container">
                <div class="dropdown_container hidden-phone">
                    <p class="text_left">SORT BY CATEGORY</p>
                    <div class="category-DD-div">
                        <v-select v-model="selected_cat" :options="dropDownCats" :searchable="false" class="open"></v-select>
                    </div>
                </div>
                <div class="alphabet-dd visible-phone">
                    <v-select v-model="selected_cat" :options="dropDownCats"></v-select>
                </div>
                
                <div class="alphabet-dd visible-phone">
                    <v-select v-model="selected_alpha" :options="alphabet"></v-select>
                </div>
          
                <ul class="store-listing text_left  padding_top_20">
                    <li v-for="store in allStores">
                        <a :href="'/stores/'+store.slug"><p class="directory_store_name">{{store.name}}</p></a>
                    </li>
                </ul>
            </div>
        </div>
        <div class="store-list-map-block col-md-8">
            <div class="main-map">
                <div id="mapsvg_store_detail">
                   <img src="http://placehold.it/2000x1000" alt="">
                </div>
            </div>
        </div>
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
                },
                consoleCallback(val) {
                    console.dir(JSON.stringify(val))
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
