---
tags: [networking, srtp, rtp]
---

# Secure Realtime Transport Protocol (SRTP)

A profile for [[realtime-transport-protocol]].

Provides encryption, message authentication and integrity, and replay attack protection of RTP data (header and payload).

Just as [[realtime-transport-protocol]] is accompanied by RTCP for transmission statistics monitoring, SRTP is accompanied by SRTCP.

All provided features in SRTP and SRTCP are optional, except for message authentication in SRTCP, meaning that they both can act as RTP and RTCP, respectively.

Use AES as default cipher, in either block or stream modes.

STRP uses key derivation to derive multiple keys used to encrypt packets. It uses a key management protocol to set up the initial master key. ZRTP and MIKEY are the two key management protocols designed to be used with SRTP.

[libsrtp](https://github.com/immunant/libsrtp) provides an implementation of all mandatory features of SRTP.