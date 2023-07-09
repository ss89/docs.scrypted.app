## Camera Preparation

Open your Camera's web administration panel or app to configure its codec settings. If your camera does not have a codec configuration tool (ie, cloud cameras such as Ring, Google, Arlo), continue on to [Adding the Camera](/add-camera).

The steps below configure the optimal settings for streaming destinations within Scrypted. Streaming destinations include HomeKit, Google Home, Alexa, Home Assistant, and [Scrypted NVR](https://demo.scrypted.app/#/demo).

## Enable Streams

Most cameras will have one one `Main Stream` and one `Substream`. Some may only have a `Main Stream`. Cameras with one `Main Stream` and two `Substreams` are ideal.
* Some cameras, such as Hikvision or Amcrest, allow more streams and higher fps when AI is disabled. The camera AI is not used within Scrypted, and can be disabled for better performance.

## Video Setup

### Enable All Streams

Enable the all available streams and substreams on the camera. Scrypted will use multiple streams, if available, for different purposes (remote streaming, analysis, etc).

### H.264 Video Codec

Set all the stream video codecs to `H.264`. Do **NOT** use `H.264+`, `Super H.264`, `H.264B`: **TURN OFF/DISABLE ALL SPECIAL VARIANTS**. Sometimes this unsupported variant setting is called `Smart Code(c)` and it should be set to `Close` or `Off`.

#### Main Stream Setup

If your camera only has a single main stream, configure it as `1920x1080`. Your camera may support a higher resolution, but without usable substreams, it is recommended to use balanced settings. Otherwise, use the max available resolution for the `Main Stream`.

|Max Resolution|Bitrate|
|-|-|
|3840x2160|8 Mbit, variable|
|2688x1520|3.5 Mbit, variable|
|1920x1080|2 Mbit, variable|

#### Sub Stream(s) Setup

|Stream|Max Resolution|Bitrate|
|-|-|-|
|Substream 1 or 2|1280x720|1 Mbit, variable|
|Substream 1 or 2|640x360|500 Kbit, variable|

## Framerate Settings

Configuring the camera frame rate involves changing two related settings: the `Frame Rate` and the `Frame Interval` (also sometimes referred to as `Keyframe Interval`, `I-Frame Interval`, or `Interframe Space`). Cameras will allow configuration either the `Interval` or `Space`. Use the settings guide below.

|Frame Rate|Interval|Space|
|-|-|-|
|20|80|4 (or 2)|

If `Frame Rate` of `20` is unavailable, `10` can be used instead.

|Frame Rate|Interval|Space|
|-|-|-|
|10|40|4 (or 2)|

### Framerate Explanation

* Any `Frame Rate` between 10 and 30 is fine, and the chosen `Frame Rate` will determine the `Frame Interval`.
* A `4 (or 2) second frequency`, aka the `Interframe Space`, can be used to compute the `Frame Interval`.
  * `Interframe Space` is the number of seconds between keyframes. `Frame Interval` is the number frames between keyframes.
  * Cameras are typically configured in `Frame Interval`. The formula for `Frame Interval` value is: `Frame Interval = 4 seconds * Frame Rate`. Examples:
    * If `Frame Rate` is `30`, `Frame Interval` should be set to `120`.
    * If `Frame Rate` is `20`, `Frame Interval` should be set to `80`.
    * If `Frame Rate` is `10`, `Frame Interval` should be set to `40`.

## Audio Setup

* Audio codecs, in order of preference:
  * Opus (used for live streaming to HomeKit or web)
  * PCM-ulaw/G711u/G711mulaw (raw format suitable for web)

Continue on to [Adding the Camera](/add-camera).