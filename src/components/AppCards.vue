<template>
    <div class="row">
        <div class="col-md-3" v-for="card in cards">
            <div class="card">
                <img class="card-img-top" :src="card.url" alt="Card image cap">
                <div class="card-body">
                    <div>
                        <h5 class="card-title">
                            <span class="view" v-if="!show">{{ card.title }}</span>
                            <span class="edit"><input v-if="show" v-model="card.title" placeholder="edit me"></span>
                            <a href="#" @click="addFavorites(card)">
                                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 576 512">
                                    <path d="M528.1 171.5L382 150.2 316.7 17.8c-11.7-23.6-45.6-23.9-57.4 0L194 150.2 47.9 171.5c-26.2 3.8-36.7 36.1-17.7 54.6l105.7 103-25 145.5c-4.5 26.3 23.2 46 46.4 33.7L288 439.6l130.7 68.7c23.2 12.2 50.9-7.4 46.4-33.7l-25-145.5 105.7-103c19-18.5 8.5-50.8-17.7-54.6zM388.6 312.3l23.7 138.4L288 385.4l-124.3 65.3 23.7-138.4-100.6-98 139-20.2 62.2-126 62.2 126 139 20.2-100.6 98z"/>
                                </svg>
                            </a>
                            <a class="edit-save" href="#" @click="show = !show" v-if="!show">
                                <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"
                                     viewBox="0 0 26 26" version="1.1" width="20px" height="20px">
                                    <g id="surface1">
                                        <path style=" "
                                              d="M 20.09375 0.25 C 19.5 0.246094 18.917969 0.457031 18.46875 0.90625 L 17.46875 1.9375 L 24.0625 8.5625 L 25.0625 7.53125 C 25.964844 6.628906 25.972656 5.164063 25.0625 4.25 L 21.75 0.9375 C 21.292969 0.480469 20.6875 0.253906 20.09375 0.25 Z M 16.34375 2.84375 L 14.78125 4.34375 L 21.65625 11.21875 L 23.25 9.75 Z M 13.78125 5.4375 L 2.96875 16.15625 C 2.71875 16.285156 2.539063 16.511719 2.46875 16.78125 L 0.15625 24.625 C 0.0507813 24.96875 0.144531 25.347656 0.398438 25.601563 C 0.652344 25.855469 1.03125 25.949219 1.375 25.84375 L 9.21875 23.53125 C 9.582031 23.476563 9.882813 23.222656 10 22.875 L 20.65625 12.3125 L 19.1875 10.84375 L 8.25 21.8125 L 3.84375 23.09375 L 2.90625 22.15625 L 4.25 17.5625 L 15.09375 6.75 Z M 16.15625 7.84375 L 5.1875 18.84375 L 6.78125 19.1875 L 7 20.65625 L 18 9.6875 Z "/>
                                    </g>
                                </svg>
                            </a>
                            <a class="edit-save" href="#" @click="show = !show" v-if="show">
                                <svg version="1.1" id="Capa_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
                                         viewBox="0 0 302.089 302.089" style="enable-background:new 0 0 302.089 302.089;" xml:space="preserve">
                                    <g>
                                        <g id="Layer_5_44_">
                                            <g>
                                                <g>
                                                    <path d="M221.209,161.634c0,2.691-2.201,4.895-4.893,4.895H55.181c-2.693,0-4.893-2.203-4.893-4.895v-3.261
                                                        c0-2.691,2.2-4.894,4.893-4.894h161.135c2.691,0,4.893,2.202,4.893,4.894V161.634z"/>
                                                </g>
                                                <g>
                                                    <path d="M149.197,200.301c0,2.691-2.201,4.895-4.892,4.895H55.182c-2.693,0-4.893-2.203-4.893-4.895v-3.261
                                                        c0-2.691,2.2-4.893,4.893-4.893h89.123c2.691,0,4.892,2.202,4.892,4.893V200.301z"/>
                                                </g>
                                                <path d="M270.764,0.001c0,0-18.179,0-24.238,0c-4.5,0-4.053,4.126-4.053,4.126v64.506c0,6.263-5.125,11.388-11.388,11.388H71.004
                                                    c-6.263,0-11.388-5.125-11.388-11.388c0,0,0-49.766,0-66.444c0-2.188-1.836-2.188-1.836-2.188H31.325c-11,0-20,9-20,20v262.088
                                                    c0,11,9,20,20,20h239.439c11,0,20-9,20-20V20C290.764,9.001,281.764,0.001,270.764,0.001z M265.043,247c0,4.95-4.05,9-9,9H46.047
                                                    c-4.95,0-9-4.05-9-9V137c0-4.95,4.05-9,9-9h209.996c4.95,0,9,4.05,9,9V247z"/>
                                                <path d="M90.28,0.001c-1.958,0-1.714,1.899-1.714,1.899v59.339c0,2.75,2.25,5,5,5h17.82c2.75,0,5-2.25,5-5V1.807
                                                    c0,0,0-1.807-1.794-1.807C108.436,0.001,96.806,0.001,90.28,0.001z"/>
                                            </g>
                                        </g>
                                    </g>
                                </svg>
                            </a>
                        </h5>
                    </div>
                    <p class="card-text view" v-if="!show">{{ card.text }}</p>
                    <textarea v-if="show" v-model="card.text" placeholder="edit me"></textarea>
                    <a href="#" class="btn btn-primary">Go somewhere</a>
                </div>
            </div>
        </div>

    </div>
</template>

<script>
  import EventBus from '../event-bus.js';
  export default {
    data () {
      return {
        show: false,
        cards: [
          {
            'title': 'News',
            'text': 'Some quick example text to build on the card title and make up the bulk of the card\'s content.',
            'url': 'https://placeholdit.co//i/250x75?bg=777777',
            'ico': '../src/assets/news.svg'
          },
          {
            'title': 'Movies',
            'text': 'Some quick example text to build on the card title and make up the bulk of the card\'s content.',
            'url': 'https://placeholdit.co//i/250x75?bg=777777',
            'ico': '../src/assets/movies.svg'
          },
          {
            'title': 'Health',
            'text': 'Some quick example text to build on the card title and make up the bulk of the card\'s content.',
            'url': 'https://placeholdit.co//i/250x75?bg=777777',
            'ico': '../src/assets/health.svg'
          },
          {
            'title': 'Medicine',
            'text': 'Some quick example text to build on the card title and make up the bulk of the card\'s content.',
            'url': 'https://placeholdit.co//i/250x75?bg=777777',
            'ico': '../src/assets/medicine.svg'
          },
          {
            'title': 'Football',
            'text': 'Some quick example text to build on the card title and make up the bulk of the card\'s content.',
            'url': 'https://placeholdit.co//i/250x75?bg=777777',
            'ico': '../src/assets/football.svg'
          },
          {
            'title': 'Tennis',
            'text': 'Some quick example text to build on the card title and make up the bulk of the card\'s content.',
            'url': 'https://placeholdit.co//i/250x75?bg=777777',
            'ico': '../src/assets/tennis.svg'
          },
          {
            'title': 'Videos',
            'text': 'Some quick example text to build on the card title and make up the bulk of the card\'s content.',
            'url': 'https://placeholdit.co//i/250x75?bg=777777',
            'ico': '../src/assets/video.svg'
          },
          {
            'title': 'Technologies',
            'text': 'Some quick example text to build on the card title and make up the bulk of the card\'s content.',
            'url': 'https://placeholdit.co//i/250x75?bg=777777',
            'ico': '../src/assets/technology.svg'
          }
        ],
        myFavorites: []
      }
    },
    methods: {
      addFavorites (card) {
        //Check if this object already exist (title is unique key)
        var isExist = (this.myFavorites).some(function (el) {
          return el.title === card.title
        });
        if (!isExist) {
          this.myFavorites.unshift(card);
        } else {
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

    .col-md-3 {
        margin: 40px 0;
    }

    .card {
        border: none;
    }

    .card svg {
        height: 20px;
        fill: #ec3d62;
    }

    .edit input {
        width: 67%;
    }

    textarea {
        margin-top: 15px;
        margin-bottom: 15px;
        height: 120px;
    }
</style>
