# Animate. Video Player

![preview](https://github.com/tpkn/animate-video-player/blob/master/preview.gif)


## Benefits
1. You could animate container the way you wish to
2. You could place container anywhere on stage
3. You could set multiple video types to make sure it would work in different browsers
4. Core is about 3.4KB



## API

### AnimateVideoPlayer(options)


### options
**Type**: _Object_  

### options.container
**Type**: _Object_  
**Default**: `false`   
Createjs object

### options.videos
**Type**: _String_ | _Array_  
**Default**: `false`   
Link to video or array of videos

### options.autoplay
**Type**: _Boolean_  
**Default**: `false`   

### options.loop
**Type**: _Boolean_  
**Default**: `false`   

### options.muted
**Type**: _Boolean_  
**Default**: `true`   

### options.preload
**Type**: _String_  
**Default**: `auto`   




### options.controls
**Type**: _Object_  
Here you can set instances of player ui    
```js
{
   play_btn     : this.pp_btn,
   sound_btn    : this.sound_btn,
   start_btn    : this.start_btn,
   replay_btn   : this.replay_btn,
   preloader_mc : this.preloader_mc,
   poster_mc    : this.poster_mc
}
```   
`start_btn` is the big play button displayed if you set `autoplay`: `false` (`play_btn` and `sound_btn` will be hidden until the video starts playing)


### options.callbacks  
**Type**: _Object_  
```js
{
   on_ready  : function(){}
   on_start  : function(){}
   on_update : function(){}
   on_end    : function(){}
   on_replay : function(){}
   on_play   : function(){}
   on_pause  : function(){}
   on_mute   : function(){}
   on_unmute : function(){}
}
```   
 



## Public

### .video
**Type**: _Object_   
Video instance

### .play()
**Type**: _Function_   

### .pause()
**Type**: _Function_   

### .stop()
**Type**: _Function_   

### .restart()
**Type**: _Function_   
Hard restart

### .mute()
**Type**: _Function_   

### .unmute()
**Type**: _Function_   

### .togglePlay()
**Type**: _Function_   

### .toggleMute()
**Type**: _Function_   





## Usage (code for Animate CC)
```javascript
var config = {
   container: this.video_mc,
   videos: ['videos/video.mp4', 'videos/video.ogg', 'videos/video.webm'],
   autoplay: true,
   loop: false,
   muted: true,
   controls: {
      play_btn: this.pp_btn,
      sound_btn: this.sound_btn,
      replay_btn: this.replay_btn,
      start_btn: this.start_btn,
      preloader_mc: this.preloader_mc,
      poster_mc: this.poster_mc
   },
   preload: 'auto',
   callbacks: {
      on_ready: function(e){
         console.log('> Callback: on_ready');
      },
      on_start: function(e){
         console.log('> Callback: on_start');
      },
      on_update: function(e){
         console.log('> Callback: on_update (' + e.target.currentTime + 'sec)');
      },
      on_end: function(e){
         console.log('> Callback: on_end');
      },
      on_replay: function(e){
         console.log('> Callback: on_replay');
      },
      on_play: function(e){
         console.log('> Callback: on_play');
      },
      on_pause: function(e){
         console.log('> Callback: on_pause');
      },
      on_mute: function(e){
         console.log('> Callback: on_mute');
      },
      on_unmute: function(e){
         console.log('> Callback: on_unmute');
      }
   }
}

/**
 * Make player instance global
 */
window.avp = new AnimateVideoPlayer(config);
```


### Config 1 (autoplay + 1 cycle + controls)
```javascript
var config = {
   container: this.video_mc,
   videos: ['videos/video.mp4', 'videos/video.ogg'],
   autoplay: true,
   muted: true,
   controls: {
      play_btn: this.pp_btn,
      sound_btn: this.sound_btn,
      replay_btn: this.replay_btn,
      preloader_mc: this.preloader_mc,
      poster_mc: this.poster_mc
   }
}
```


### Config 2 (autoplay + looped + no controls)
```javascript
var config = {
   container: this.video_mc,
   videos: ['videos/video.mp4', 'videos/video.ogg'],
   autoplay: true,
   loop: true
}
```




## PS
Not tested enough on mobile OS


## Changelog 
#### v1.3.0 (2018-05-19):
- added support of big `play` button

#### v1.2.5 (2017-11-19):
- Added `stop` method

#### v1.0.1 (2017-08-17):
- Fixed bug when function using `canPlayType()` returns `null` if video path doesn't have an extension. Now all media sources are placed in separate `<source>` tags.
