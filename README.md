# React H5 Audio Player

* Audio player component that provides consistent UI/UX on different browsers.
* Flexbox layout with SVG icons. Mobile friendly.
* Accessibility supported, keyboards events supported.
* Written in TypeScript.

![screenshot](./screenshot.png)

Live Demo: [Storybook](https://static.hanzluo.com/react-h5-audio-player-storybook/index.html?path=/docs/layouts--default-story)

Website example: [hanzluo.com](https://hanzluo.com/#music) | [Code](https://github.com/lhz516/hanzluo/blob/3a1de210bb8de72ef2def5a6216b58108088e131/src/components/home/home.js#L281)

Supported browsers: Chrome, Firefox, Safari, Opera, Edge, IE (≥10)

## Installation

`$ npm i react-h5-audio-player`

Or

`$ yarn add react-h5-audio-player`

## Usage

```jsx
import AudioPlayer from 'react-h5-audio-player';
import 'react-h5-audio-player/lib/styles.css';
// import 'react-h5-audio-player/lib/styles.less' Use LESS
// import 'react-h5-audio-player/src/styles.scss' Use SASS

const Player = () => (
  <AudioPlayer
    autoPlay
    src="http://example.com/audio.mp3"
    onPlay={e => console.log("onPlay")}
    // other props here
  />
);
```

#### Keyboard shortcuts (Player focused)
| Key binding | Action |
| ----------- | ------ |
| Space       | Play/Pause |
| ←           | Rewind |
| →           | Forward |
| ↑           | Volume up |
| ↓           | Volume down |
| L           | Toggle loop |
| M           | Toggle mute |

## Props

### HTML Audio Tag Native Attributes

| Props       |  Type   |  Default  | Note                 |
| ----------- | ------- | --------- | ---------------------|
| src         | string  | ''        |                      |
| preload     | string  | 'auto'    |                      |
| autoPlay    | boolean | false     | Won't work on mobile |
| loop        | boolean | false     |                      |
| muted       | boolean | false     |                      |
| loop        | boolean | false     |                      |
| volume      | number  | 1.0       | Won't work on mobile |
| crossOrigin | string  | undefined |                      |
| mediaGroup  | string  | undefined |                      |


More native attributes detail: [MDN Audio element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/audio)

The `controls` attribute defaults to `false` and should never be changed to `true` because this library is already providing UI.

### Other Props

| Props                  | Type              | Default | Note |
| ---------------------- | ----------------- | ------- | ---- |
| showVolumeControl      | boolean           | true    | Show volume bar and mute button |
| showLoopControl        | boolean           | true    | Show loop toggle button | 
| showSkipControls       | boolean           | false   | Show Previous/Next buttons |
| showJumpControls       | boolean           | true    | Show Rewind/Forward buttons |
| showDownloadProgress   | boolean           | true    | Show download progress over progress bar |
| onClickPrevious        | Function (Event)  | null    | Called when click Previous button |
| onClickNext            | Function (Event)  | null    | Called when click Next button |
| onPlayError            | Function (Error)  | null    | Called when there's error invoking `audio.play()`, it captures error that `onError` won't catch |
| volumeJumpStep         | number            | 0.1     | Indicates the volume jump step when pressing up/down arrow key, volume range is `0` to `1` |
| progressJumpStep       | number            | 5000    | Indicates the progress jump step (ms) when clicking rewind/forward button or left/right arrow key|
| progressUpdateInterval | number            | 20      | Indicates the interval (ms) that the progress bar UI updates,  |
| listenInterval         | number            | 1000    | Indicates the interval (ms) to call the `onListened` prop during playback |
| onListen               | Function (number) | null    | Called every `listenInterval` milliseconds during playback |
| onPlay                 | Function (Event)  | null    | Called when user plays the audio |
| onPause                | Function (Event)  | null    | Called when user pauses the audio |
| onAbort                | Function (Event)  | null    | Called when unloading the audio player, like when switching to a different src file |
| onCanPlay              | Function (Event)  | null    | Called when enough of the file has been downloaded to be able to start playing |
| onCanPlayThrough       | Function (Event)  | null    | Called when enough of the file has been downloaded to play through the entire file |
| onEnded                | Function (Event)  | null    | Called when playback has finished to the end of the file |
| onError                | Function (Event)  | null    | Called when the audio tag encounters an error |

## UI Overwrites

React H5 Audio Player provides built-in class names and SASS/LESS variables for developers to overwrite.

### SASS variables

```scss
$rhap_theme-color: #868686 !default;
$rhap_background-color: #fff !default;
$rhap_bar-color: #e4e4e4 !default;
$rhap_time-color: #333 !default;
$rhap_font-family: inherit !default;
```

For LESS variables, just replace `$` with `@`.

## Advanced Usage

### Access to the audio element

You can get direct access to the underlying audio element. First get a ref to ReactAudioPlayer:

```jsx
<ReactAudioPlayer ref={c => (this.player = c)} /> // Using `createRef` also works
```

Then you can access the audio element like this:

`this.player.audio`

## Release Notes

https://github.com/lhz516/react-h5-audio-player/releases

### Breaking changes from 1.x to 2.x

- Removed inline styles, import `css`, `scss` or `less` manually
- Removed props `hidePlayer` - Use parent logic to hide player
- Removed props `onDragStart`, `onDragMove`, `onDragEnd` - V2 isn't using drag events anymore

### Breaking changes from 0.x to 1.x

In 1.x, we use `prop-types` package instead of using it directly in React. Thus we dropped support under `react@15.5.0`. The usage will remain the same.


## How to contribute

Issues and PR's are welcome.

## Credits

- Inspired by [React Audio Player](https://github.com/justinmc/react-audio-player).
- Icon wrapper [iconify](https://iconify.design/)
- Icons [Material Design Icons](https://github.com/Templarian/MaterialDesign)
