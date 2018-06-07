<template>
    <div class="row">
        <div class="col-md-3" v-for="card in cards">
            <div class="card">
                <img class="card-img-top" :src="card.url" alt="Card image cap">
                <div class="card-body">
                    <div>
                        <h5 class="card-title">
                            {{ card.title }}
                            <a href="#" @click="addFavorites(card)">
                                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 576 512">
                                    <path d="M528.1 171.5L382 150.2 316.7 17.8c-11.7-23.6-45.6-23.9-57.4 0L194 150.2 47.9 171.5c-26.2 3.8-36.7 36.1-17.7 54.6l105.7 103-25 145.5c-4.5 26.3 23.2 46 46.4 33.7L288 439.6l130.7 68.7c23.2 12.2 50.9-7.4 46.4-33.7l-25-145.5 105.7-103c19-18.5 8.5-50.8-17.7-54.6zM388.6 312.3l23.7 138.4L288 385.4l-124.3 65.3 23.7-138.4-100.6-98 139-20.2 62.2-126 62.2 126 139 20.2-100.6 98z"/>
                                </svg>
                            </a>
                        </h5>
                    </div>
                    <p class="card-text">{{ card.text }}</p>
                    <a href="#" class="btn btn-primary">Go somewhere</a>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
  import EventBus from '../event-bus.js'
  export default {
    data: function () {
      return {
        cards: [
          {
            title: 'News',
            text: 'Some quick example text to build on the card title and make up the bulk of the card\'s content.',
            url: 'https://placeholdit.co//i/80x80?bg=777777',
            ico: '../src/assets/news.svg'
          },
          {
            title: 'Movies',
            text: 'Some quick example text to build on the card title and make up the bulk of the card\'s content.',
            url: 'https://placeholdit.co//i/80x80?bg=777777',
            ico: '../src/assets/movies.svg'
          },
          {
            title: 'Health',
            text: 'Some quick example text to build on the card title and make up the bulk of the card\'s content.',
            url: 'https://placeholdit.co//i/80x80?bg=777777',
            ico: '../src/assets/health.svg'
          },
          {
            title: 'Medicine',
            text: 'Some quick example text to build on the card title and make up the bulk of the card\'s content.',
            url: 'https://placeholdit.co//i/80x80?bg=777777',
            ico: '../src/assets/medicine.svg'
          },
          {
            title: 'Football',
            text: 'Some quick example text to build on the card title and make up the bulk of the card\'s content.',
            url: 'https://placeholdit.co//i/80x80?bg=777777',
            ico: '../src/assets/football.svg'
          },
          {
            title: 'Tennis',
            text: 'Some quick example text to build on the card title and make up the bulk of the card\'s content.',
            url: 'https://placeholdit.co//i/80x80?bg=777777',
            ico: '../src/assets/tennis.svg'
          },
          {
            title: 'Videos',
            text: 'Some quick example text to build on the card title and make up the bulk of the card\'s content.',
            url: 'https://placeholdit.co//i/80x80?bg=777777',
            ico: '../src/assets/video.svg'
          },
          {
            title: 'Technologies',
            text: 'Some quick example text to build on the card title and make up the bulk of the card\'s content.',
            url: 'https://placeholdit.co//i/80x80?bg=777777',
            ico: '../src/assets/technology.svg'
          }
        ],
        myFavorites: []
      }
    },
    methods: {
      addFavorites: function (card) {
        //Check if this object already exist (title is unique key)
        var isExist = (this.myFavorites).some(function (el) {
          return el.title === card.title
        });
        if (!isExist) {
          this.myFavorites.unshift(card);
        }else {
          alert('You already include this card!');
        }
        //Create var ~myFav and send it to mounted EventBus!
        var myFav = this.myFavorites;
        EventBus.$emit('favorites', myFav);
      }
    }
  }
</script>

<style scoped>
    .col-md-3{
        margin: 40px 0;
    }
    .card{
        border: none;
    }

    .card svg{
        height: 20px;
        fill: #ec3d62;
    }
</style>