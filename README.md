# unified-user-data-format

Specification for the unified user data format across the various "Tube" apps (NewPipe, FreeTube, Invidious, etc..)

## Intro

* This specification is a very early draft, and prone to regular changes
* Unless otherwise specified, all fields are assumed to be `Strings`


## Main file (`main.json`)

#### `"version"`

The [semantic version](https://semver.org/) of the specification.

Conditions for bumping major/minor/patch version: TBD
Potential suffixes: `-draft`, TBD

#### `"subscriptions"`

An array of Subscription objects. See below for details.

#### `"playlists"`

An array of Strings.

Each string refers to the name of a playlist file (without the `playlist_` prefix)
that was included in the export.

#### `"watch_history_present"`

A Boolean.

Indicates whether the special playlist `watch_history` was included in the export.

### Overview

```javascript
{
	"version": "X.Y.Z[-draft/-rc]",
	"watch_history_present": Boolean,
	"subscriptions": Subscriptions[],
	"playlists": String[],
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


## Playlist file (`playlist_xxx.json`)

A playlist file MUST contain the data of a single playlist created by the user.

#### > `"name"`

The title of the playlist.

#### > `"visibility"`

The visibility of the playlist.

Accepted values: "public", "unlisted", "private"

#### > `"description"`

The description of the playlist.
Format: plain text (? TBD)

CAN be nil; In this case, the parser MUST assume an empty `String`.

#### > `"videos"`

An array of `String`.

Each item of the array is an URL representing one video in the playlist.
The array must be sorted in the same order as the videos in the playlist.

### Overview

```javascript
{
	"name": String,
	"visibility": String,
	"description": String,
	"videos": String[],
}
```


## Watch history file (`watch_history.json`)

The watch history is nothing more than a private paylist, without metadata

#### > `"videos"`

An array of `String`.

Each item of the array is an URL representing one video in the playlist.
The array must be sorted in the same order as the videos in the playlist.

### Overview

```javascript
{
	"videos": String[],
}
```
