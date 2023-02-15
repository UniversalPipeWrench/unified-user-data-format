# unified-user-data-format

Specification for the unified user data format across the various "Tube" apps (NewPipe, FreeTube, Invidious, etc..)

## Intro

* This specification is a very early draft, and prone to regular changes
* Unless otherwise specified, all fields are assumed to be `Strings`


## Top level structure

#### `"version"`

The [semantic version](https://semver.org/) of the specification.

Conditions for bumping major/minor/patch version: TBD
Potential suffixes: `-draft`, TBD

#### `"subscriptions"`

An array of Subscription objects. See below for details.

#### `"playlists"`

An array of Playlist objects. See below for details.

### Overview

```javascript
{
	"version": "X.Y.Z[-draft/-rc]",
	"subscriptions": Subscriptions[],
	"playlists": Playlist[],
}
```

## Subscription object

#### > `"name"`

The name of the subscribed channel.

#### > `"url"`

The URL used to access the user subscribed channel.

#### > `"thumbnail"`

The URL to the user/channel's thumbnail.

### Example

```javascript
{
  "name": "Linus Tech Tips",
  "url": "https://www.youtube.com/channel/UCXuqSBlHAE6Xw-yeJA0Tunw",
  "thumbnail": "https://yt3.ggpht.com/ytc/abcdef..."
}
```

## Playlist object

#### > `"name"`

The title of the playlist.

#### > `"visibility"`

The visibility of the playlist.

Accepted values: "public", "unlisted", "private"

#### > `"description"`

The description of the playlist.
Format: plain text (? TBD)

CAN be ommited; In this case, the parser MUST assume an empty `String`.

#### > `"videos"`

An array of `String`.

Each item of the array is an URL representing one video in the playlist.
The array must be sorted in the same order as the videos in the playlist.

### Example

```javascript
{
  "name": "My fav Music!",
  "visibility": "public",
  "description": "The playlist I listen to every day",
  "videos": [
    "https://www.youtube.com/v/djV11Xbc914",
    "https://www.youtube.com/v/HEXWRTEbj1I",
    "https://www.youtube.com/v/sRl02nXVMhw",
    "https://www.youtube.com/v/dQw4w9WgXcQ",
    "https://www.youtube.com/v/Hy8kmNEo1i8",
    "https://www.youtube.com/v/zA52uNzx7Y4",
    "https://www.youtube.com/v/9bZkp7q19f0"
  ]
},
```
