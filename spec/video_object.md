# Video object

#### > `"type"`

The type of the service this entry refers to.

This field is a short and meaningful identifier that prevents the parser from
trying to guess the name of the service from the `url` present in this object.

#### > `"id"`

The ID of the video.

The format if this ID is service-dependant.

The only requirement being the uniqueness of the ID in the service.
E.g: All youtube video IDs (11 character long) are unique to eachother.

#### > `"url"`

The URL used to access the video.

This URL SHOULD NOT contain query parameters.

#### > `"thumbnail"`

The URL to the video's thumbnail.

This field CAN be omitted, e.g if the video doesn't have a thumbnail, or
if the exporter doesn't store this metadata.

If present, it MUST represent the original URL to the thumbnail as found on
the service mentioned in `type`.

### Overview

```javascript
{
  "type": String,
  "id": String,
  "url": String,
  "thumbnail": String | null
}
```
