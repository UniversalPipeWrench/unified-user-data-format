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

An array of [subscription objects](spec/subscription_object).

#### `"playlists"`

An array of Strings.

Each string refers to the name of a playlist file (without the `playlist_` prefix)
that was included in the export.

#### `"saved_playlists_present"`

A Boolean.

Indicates whether the `saved_playlists.json` file was included in the export.

#### `"watch_history_present"`

A Boolean.

Indicates whether the special playlist `watch_history` was included in the export.

### Overview

```javascript
{
	"version": "X.Y.Z[-draft/-rc]",
	"saved_playlists_present": Boolean,
	"watch_history_present": Boolean,
	"subscriptions": SubscriptionObject[],
	"playlists": String[],
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

An array of [video objects](spec/video_object).

### Overview

```javascript
{
	"name": String,
	"visibility": String,
	"description": String,
	"videos": VideoObject[],
}
```


## Saved playlist file (`saved_playlists.json`)

This file contains the playlists from other services that the user bookmarked.

#### > `"playlists"`

An array of [saved playlist objects](spec/saved playlist_object).

### Overview

```javascript
{
	"playlists": SavedPlaylist[],
}
```


## Watch history file (`watch_history.json`)

The watch history is nothing more than a private paylist, without metadata

#### > `"videos"`

An array of [video objects](spec/video_object).

### Overview

```javascript
{
	"videos": VideoObject[],
}
```
