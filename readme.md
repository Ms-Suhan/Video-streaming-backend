# Welcomet to the video streaming app

## This is a simple video streaming app that allows you to upload and watch videos.

## Features:
- Upload videos
- Watch videos

## Technologies used:
- [FFmpeg](https://ffmpeg.org/download.html)
- Node.js
- Express.js
- React.js


## File Structure Tree:



|── video-streaming-backend/

    ├── frontend/
    │   ├── public
    │   └── src/
    │       ├── assets
    │       ├── App.jsx
    │       ├── main.jsx
    │       ├── App.css
    │       └── VideoPlayer.jsx
    ├── uplaods/
    │   └── courses
    ├── index.js
    ├── package.json
    └── readme.md

## HTTP Live Streaming (HLS)
 - HLS, or HTTP Live Streaming, is a widely used protocol for delivering video and audio streams over the internet. It functions for both live and on-demand streaming scenarios.

## Advantages of HLS
 - Broad Device Compatibility: Since HLS leverages HTTP, inherently compatible with most devices. This simplifies implementation compared to protocols requiring specialized servers.
 - Adaptive Bitrate Streaming: HLS can adjust video quality based on network conditions, ensuring uninterrupted playback even with fluctuating bandwidth. This is why video quality can change mid-stream.
 - 
#### How HLS Works

### Server-side Processing

- Encoding: Video data is reformatted for universal recognition using H.264 or H.265 encoding.
- Segmenting: The video is chopped into short segments, typically a few seconds long.
- Index File Creation: An index file keeps track of the segment order for proper playback assembly.
- Multi-Quality Copies: HLS creates multiple copies of the segmented video at different quality levels (e.g., 480p, 720p, 1080p).
- Distribution: Encoded segments are delivered to client devices upon requesting the stream. Content Delivery Networks (CDNs) often aid in geographically dispersed distribution and caching for faster serving.

  
## Client-side Playback

- Client Devices: These receive and play the stream (e.g., smartphones, laptops).
- Video Assembly: Client devices use the index file to assemble the video in the correct order.
- Adaptive Quality Switching: The client can switch between quality levels (higher to lower or vice versa) based on network conditions.


## Adaptive Bitrate Streaming in HLS

A key feature of HLS is adaptive bitrate streaming, allowing video quality adjustments mid-stream based on network fluctuations. This ensures smooth playback even with variable bandwidth.

## Transport Protocol: TCP vs UDP

TCP and UDP are transport protocols responsible for delivering content over the internet. TCP prioritizes reliable data delivery, while UDP offers faster transmission but may lose data in transit. Unlike some streaming protocols that utilize UDP for speed, HLS relies on TCP for several reasons:

 - HTTP dependency: HLS operates over HTTP, built for TCP usage (with some exceptions).
 - Improved Internet Reliability: Modern internet infrastructure is more reliable and efficient, handling video frame delivery effectively.
 - Adaptive Bitrate Compensation: Adaptive bitrate streaming mitigates potential slowdowns from TCP.
 - Non-Real-Time Streaming: Unlike video conferencing requiring real-time interaction, a few seconds of lag in HLS doesn't significantly impact user experience compared to missing video frames.
   
### Other Streaming Protocols

Several protocols share similarities with HLS, including MPEG-DASH and HDS, which also function over HTTP and offer adaptive bitrate streaming. Adobe Flash, previously dominant and reliant on RTMP or HDS for video streaming, has declined due to diminishing browser support. While RTMP remains in use, its support is also on the decline.
