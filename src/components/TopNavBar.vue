<template>
    <div class="container-fluid">
        <nav class="navbar navbar-expand-lg navbar-light bg-light">
            <a class="navbar-brand" href="#">Vue.js Favorites App</a>
            <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav">
                    <li class="nav-item active">
                        <a class="nav-link" href="#">Home <span class="sr-only">(current)</span></a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#">Features</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#">Pricing</a>
                    </li>
                </ul>
            </div>
            <div class="collapse navbar-collapse" id="navbarSupportedContent" >
                <ul class="navbar-nav ml-auto">
                    <a class="nav-link" href="#" @click="showFavorites = !showFavorites">My Favorites</a>
                </ul>
            </div>
        </nav>

           <div class="favorites-holder">
               <ul class="favorites" v-if="showFavorites" transition-group="expand">
                   <li v-for="fav in myFavs" class="fav-item" @click="removeFromFavorites">
                       <a href="#" class="fav-link">
                           <img :src="fav.ico" alt="">
                           {{ fav.title }}
                       </a>
                   </li>
               </ul>
           </div>

    </div>
</template>

<script>
  import EventBus from '../event-bus.js';
  export default {
    data: function () {
      return {
        showFavorites: true,
        myFavs: []
      }
    },
    methods: {
      removeFromFavorites: function (index) {
        if(confirm("Are you sure ?")) {
          this.myFavs.splice(index, 1);
        }
      }
    },
    mounted () {
      // You should use arrow function if you want to get parameteres outside mounted function!
      EventBus.$on('favorites',(myFav) => {
        this.myFavs = myFav;
      });
    }
  }
</script>

<style scoped>
    .navbar{
        width: 100%;
        left: 0;
        z-index: 9999;
    }
    .favorites-holder{
        background-color: #ddd;
        opacity: 0.7;
        width: 100%;
    }

    .favorites-holder ul{
        display: flex;
        list-style-type: none;
        padding: 0;
    }

    .favorites-holder ul li {
        padding: 20px;
        font-size: 20px;
    }
    .favorites-holder ul li a{
        color: #212529;
        font-weight: 400;
        text-decoration: none;
    }

    .favorites-holder img{
        height: 35px;
        display: block;
        margin: auto;
    }
    /* always present */
    .expand-transition {
        transition: all .3s ease;
        height: 30px;
        padding: 10px;
        background-color: #eee;
        overflow: hidden;
    }
    /* .expand-enter defines the starting state for entering */
    /* .expand-leave defines the ending state for leaving */
    .expand-enter, .expand-leave {
        height: 0;
        padding: 0 10px;
        opacity: 0;
    }
</style>