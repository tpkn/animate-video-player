# Animate Video Player

![preview](https://github.com/tpkn/animate-video-player/blob/master/preview.gif)


### Benefits
1. You could animate container the way you wish to
2. You could place container anywhere on stage
3. You could set multiple video types to make sure it would work in different browsers
4. Core is about 3.4KB
<br />

### PS
Not tested enough on mobile OS
<br />

### Usage (code for Animate CC)
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
<br />

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
<br />

### Config 2 (autoplay + looped + no controls)
```javascript
var config = {
   container: this.video_mc,
   videos: ['videos/video.mp4', 'videos/video.ogg'],
   autoplay: true,
   loop: true
}
```
<br />

### Public methods
| Method | Type | Description |
|-------------|:-------------:|-------------|
| video | Object | Video instance |
| play | Function | - |
| pause | Function | - |
| stop | Function | - |
| restart | Function | Hard restart video |
| mute | Function | - |
| unmute | Function | - |
| togglePlay | Function | - |
| toggleMute | Function | - |
<br />

### Basic settings (config)
| Option | Type | Default | Description |
|-------------|:-------------:|:-------------:|-------------|
| container | Object | - | CreateJS object |
| videos | Array / String | - | Link to video or array of link |
| autoplay | Boolean | false | - |
| loop | Boolean | false | - |
| muted | Boolean | true | - |
| preload | String | 'auto' | - |
<br />

### Callbacks (config.callbacks)
| Option | Type | Default | Description |
|-------------|:-------------:|:-------------:|-------------|
| on_ready | Function | - | - |
| on_start | Function | - | - |
| on_update | Function | - | - |
| on_end | Function | - | - |
| on_replay | Function | - | - |
| on_play | Function | - | - |
| on_pause | Function | - | - |
| on_mute | Function | - | - |
| on_unmute | Function | - | - |
<br />

### UI (config.controls)
| Option | Type | Default | Description |
|-------------|:-------------:|:-------------:|-------------|
| play_btn | Object | - | CreateJS object (with 2 frames for each state) |
| sound_btn | Object | - | CreateJS object (with 2 frames for each state) |
| replay_btn | Object | - | CreateJS object |
| preloader_mc | Object | - | CreateJS object (with looped animation) |
| poster_mc | Object | - | CreateJS object (with poster image) |
<br />

## Changelog 2017-08-17:
- Fixed bug when function using `canPlayType()` returns `null` if video path doesn't have an extension. Now all media sources are placed in separate `<source>` tags.
