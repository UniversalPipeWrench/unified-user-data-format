# Subscription object

#### > `"type"`

The type of the service this entry refers to.

This field is a short and meaningful identifier that prevents the parser from
trying to guess the name of the service from the `url` present in this object.

#### > `"id"`

The ID of the subscribed channel.

The format if this ID is service-dependant.

The only requirement being the uniqueness of the ID in the service.
E.g: All youtube channel IDs (starting with `UC`) are unique to eachother.

#### > `"name"`

The name of the subscribed channel.

#### > `"url"`

The URL used to access the user subscribed channel.

This URL SHOULD NOT contain query parameters.

#### > `"thumbnail"`

The URL to the user/channel's thumbnail.

### Overview

```javascript
{
  "type": String,
  "id": String,
  "name": String,
  "url": String,
  "thumbnail": String
}
```
