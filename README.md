# Geetest Device Fingerprint Tester

A single-page web tool for testing the Geetest device fingerprint SDK (`gd.js`). It generates a `geeToken` in the browser and composes a sample JSON payload that mirrors what a backend would send to the Geetest risk API.

Traditional Chinese version: [README.zh-TW.md](./README.zh-TW.md)

## Features

- Initialize the Geetest device fingerprint SDK with a configurable App ID
- Collect common request fields (user IP, scene, optional user ID / ID type) through a simple form
- Call `initGeeGuard` and surface the returned `gee_token` or error payload
- Preview the composed request body as syntax-highlighted JSON
- One-click copy of the generated JSON for pasting into API clients

## Scenes supported

`login`, `sign_up`, `activity`

## User ID types supported

Phone (`2`), MD5 Phone (`102`), QQ OpenID (`3`), Wechat OpenID (`4`)
