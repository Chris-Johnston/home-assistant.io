---
layout: page
title: "Microsoft Face Detect"
description: "Instructions on how to integrate Microsoft Face Detect into Home Assistant."
date: 2017-01-25 00:00
sidebar: true
comments: false
sharing: true
footer: true
logo: microsoft.png
ha_category:
  - Image Processing
ha_release: 0.38
redirect_from:
 - /components/image_processing.microsoft_face_detect/
---

The `microsoft_face_detect` image processing platform allows you to use the
[Microsoft Face Identify](https://www.microsoft.com/cognitive-services/en-us/)
API through Home Assistant. This platform enables you do detect face on camera
and fire an event with attributes.

Please refer to the [Microsoft Face component](/components/microsoft_face/) configuration on
how to setup the API key.

For using the result inside an automation rule,
take a look at the [Image Processing component](/components/image_processing/) page.

<p class='note'>
The free version of the Microsoft Face identify API limits the number of requests possible per month. Therefore, it is strongly recommended that you limit the `scan_interval` when setting up an instance of this entity as detailed on the main [Image Processing component](/components/image_processing/) page.
</p>

### Configuration

```yaml
# Example configuration.yaml entry
image_processing:
  - platform: microsoft_face_detect
    source:
      - entity_id: camera.door
```

{% configuration %}
confidence:
  description: The minimum of confidence in percent to process with Home Assistant.
  required: false
  type: integer
  default: 80
source:
  description: List of image sources.
  required: true
  type: list
  keys:
    entity_id:
      description: A camera entity id to get picture from.
      required: true
      type: string
    name:
      description: This parameter allows you to override the name of your `image_processing` entity.
      required: false
      type: string
attributes:
  description: "The image search attributes. Supported: `age`, `gender`, `glasses`."
  required: false
  type: list
  default: "[age, gender]"
{% endconfiguration %}
