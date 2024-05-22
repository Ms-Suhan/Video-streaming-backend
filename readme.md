# Welcome to the video streaming app - Prototype

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

    
# Live Streaming

Live streaming refers to transmitting video content over the internet in real-time. Unlike regular streaming where videos are prerecorded, live streaming captures and broadcasts video as it happens. Think of it as the difference between a pre-recorded lecture and a live presentation.

Here's a breakdown of live streaming technology:

## Behind the Scenes

 - **Video Capture**: The process starts with capturing raw video data using a camera. This visual information is converted into digital data (1s and 0s).

 - **Compression and Encoding:**

    - **Compression**: Reduces redundant data. For example, if the background remains unchanged in consecutive frames, it only needs to be encoded once.
    - **Encoding**: Converts the data into a format compatible with various devices (e.g., H.264, H.265).
 - **Segmentation**: The video is chopped into short segments (a few seconds each) for efficient transmission.

 - **CDN Distribution and Caching**:

    - **CDN (Content Delivery Network):** A network of geographically distributed servers that cache and deliver content.
    - **Distribution:** The CDN distributes the segmented video to viewers. Users' requests are directed to nearby CDN servers for faster performance compared to the origin server (where the stream originates).
    - **Caching:** CDN servers temporarily store (cache) video segments, reducing latency for viewers by delivering data from the cache instead of the origin server.
 - **Decoding and Playback:**

    - Users' devices receive, decode, and decompress the video segments.
    - Media players on the devices interpret the data and display the video.


### Example: Alice's Live Stream

Imagine Alice starts a live stream on her smartphone, and viewers like Bob across the country tune in. Here's what happens:

    1.Alice's phone captures a video segment (e.g., her saying "Hello, world!").
    2.The segment is compressed and encoded.
    3.The encoded data is sent to the CDN.
    4.Bob's phone, located near a CDN server, requests the video segment.
    5.The CDN server delivers the cached segment to Bob's phone.
    6.Bob's phone decodes the data and displays the video.

    
**Why CDNs are Important for Live Streaming**

 - **Bandwidth Management:** CDNs prevent choke points (slowdowns) on the origin server's network by distributing the streaming load.
 - **Global Content Delivery:** CDNs ensure smooth delivery worldwide by having servers closer to viewers.
 - **Reduced Latency:** Delivering content from nearby CDN servers reduces round-trip time (RTT) and latency for viewers.
 - **Workload Distribution:** CDNs share the workload of serving video data, reducing strain on the origin server.
 - **Caching:** CDN caching minimizes latency by delivering data from the cache instead of the origin server, even though it introduces a slight delay.
   
In essence, CDNs are crucial for live streaming by ensuring efficient, high-quality video delivery to a global audience with minimal lag.
    

## HTTP Live Streaming (HLS)
 - HLS, or HTTP Live Streaming, is a widely used protocol for delivering video and audio streams over the internet. It functions for both live and on-demand streaming scenarios.

   

## Advantages of HLS
 - Broad Device Compatibility: Since HLS leverages WHTTP, inherently compatible with most devices. This simplifies implementation compared to protocols requiring specialized servers.
 - Adaptive Bitrate Streaming: HLS can adjust video quality based on network conditions, ensuring uninterrupted playback even with fluctuating bandwidth. This is why video quality can change mid-stream.


   
#### How HLS Works

### Server-side Processing

- **Encoding:** Video data is reformatted for universal recognition using H.264 or H.265 encoding.
- **Segmenting:** The video is chopped into short segments, typically a few seconds long.
- **Index File Creation:** An index file keeps track of the segment order for proper playback assembly.
- **Multi-Quality Copies:** HLS creates multiple copies of the segmented video at different quality levels (e.g., 480p, 720p, 1080p).
- **Distribution:** Encoded segments are delivered to client devices upon requesting the stream. Content Delivery Networks (CDNs) often aid in geographically dispersed distribution and caching for faster serving.

  
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
