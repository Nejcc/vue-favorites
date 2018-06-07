# vue-favorites

> A Vue.js project

> This Vue app shows how we can send information between two non-parent/child components, and how to add the selected items into json.
> Also you can understand how to get clicked object from array of objects.

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build
```

For detailed explanation on how things work, consult the [docs for vue-loader](http://vuejs.github.io/vue-loader).


## EventBus to communicate between Vue.js components

``` bash
# In both components AppCards and TopNavBar we import EvenBus file
import EventBus from '../event-bus.js'

# In AppCards Component we called addFavorites method, it emit new event 
# with name 'favorites' and pass 'myFav' with it.
EventBus.$emit('favorites', myFav);

# In TopNavBar Component we register listener which listens for event 'favorites' 
# to be transported using EventBus.
# When the event appears we can use myFav which we recieved as argument.

mounted () {
  // You should use arrow function if you want to get parameteres outside mounted function!
  EventBus.$on('favorites',(myFav) => {
    // Save all changes into 'myFavs' prop
    this.myFavs = myFav;
  });
}    
```

## How to get clicked element like object from array of objects

``` bash
# With v-for we itterate over 'cards' array which is created in our 'data'
v-for="card in cards"

# Inside of this for loop we create @click event "addFavorites(card)" and 
# pass every clicked element as object with , where card  is an alias for 
# the array element being iterated on!
@click="addFavorites(card)"
```
