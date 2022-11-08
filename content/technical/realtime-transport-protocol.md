---
tags: [networking, rtp]
---

# Realtime Transport Protocol (RTP)

A network protocol for transferring audio and video.

Typically runs over UDP.

Runs in conjunction with RTP Control Protocol (RTCP).
RTCP is used to monitor transmission statistics of RTP, and sync multiple streams. 
RTP carries the stream itself.

Detects packet loss and out-of-order delivery.

RTP has profiles and payload formats. Every instantiation of RTP in an application requres a profile and at least one payload format spec.

The profile says how to encode payload data.

[[secure-realtime-transport-protocol]] is an example of a profile.