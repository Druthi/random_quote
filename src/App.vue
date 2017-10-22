<template>
  
  <div id="app"> 
          
        <button type="submit" v-on:click= "display">Click me!</button>
          <div v-html= "result">
          </div> 
        <!--<button type="submit" v-on:click= "postTweet">Post to Twitter!</button>-->
        
      
    
  </div>
</template>

<script>


export default {
  name: 'app',
  data() {
    return{
      results: [],
      result: "",
      tweet:{
        status:this.result 
        }
    }
  },
  methods: {
    display: function(){
      var randomNumber = Math.floor(Math.random() * this.results.length);
      this.result = this.results[randomNumber].content;
    }

    //postTweet: function(){
  //
    //  var Twit = require('twit')
    //
    //  var T = new Twit({
    //    consumer_key:         'CECB6gJaB6jxneFSeu2FHb89w',
    //    consumer_secret:      'xJQrhSOK4WLTIwyMsBgk19xo4Oj1DRs4UrwrmV6IcEgSUZw02d',
    //    access_token:         '2838236923-Zhh0BkqcIXSVs2nA0PAmMmKbzca4AdpbmVWHwux',
    //    access_token_secret:  'QmWWTXQojX7ZQ5U7v7Rzs7G9HO6ESrwUA3AmibJQdRBXe',
  //
    //  });
//
//
    //  T.post('statuses/update', this.tweet, this.tweeted());
    //},
    //  
    //tweeted: function(err, data, response) {
    //  console.log(data);
    //} 
  },
   
  created: function(){
    this.$http.get('http://quotesondesign.com/wp-json/posts?filter[orderby]=rand&filter[posts_per_page]=10')
      .then(response=> {
      this.results = response.data;
      console.log(this.results);
    });
  }

  
   
}
</script>

<style scoped>
#app {
  }
</style>


