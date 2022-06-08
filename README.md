# GDIndex
Forked version of [mapple3142/GDIndex](https://github.com/maple3142/GDIndex)

![preview](https://i.imgur.com/ENkZwCU.png)

[繁體中文](README.zhtw.md)
[简体中文](README.zh.md)

> GDIndex is a similar project to [GOIndex](https://github.com/donwa/goindex).
> It allows you to deploy a "Google Drive Index" on Cloudflare's Workers along with many extra features.
>
> Instead of modifying GOIndex, GDIndex is a complete rewrite from scratch.

[Demo](https://gdindex-demo.maple3142.workers.dev/)

## The differences between GOIndex and GDIndex

-   Front-end is based on Vue.js
-   Image viewer doesn't require opening new page
-   Video player support subtitles(Currently only srt is supported)
-   Online PDF, EPUB reader
-   No directory-level password protection(.password)
-   Support Http Basic Auth
-   Support multiple drives(personal, team) without changing server's code

## How to Use

### Simple
Go [https://gdindex-code-builder.maple3142.net/](https://gdindex-code-builder.maple3142.net/), and follow the instructions there.

### Manual
1. Install [rclone](https://rclone.org/)
2. Setup your Google Drive: https://rclone.org/drive/
3. Run `rclone config file` to find your `rclone.conf` location
4. Find `refresh_token` in your `rclone.conf`, and `root_folder_id` too(optionally).
5. Copy the content of [worker/dist/worker.js](worker/dist/worker.js) to CloudFlare Workers.
6. Fill `refresh_token`, `root_folder_id` and other options on the top of the script.
7. Deploy!

### Using service accounts

1. Create a service account, a corresponding service account key, and get the JSON from the [Google Cloud Platform console](https://cloud.google.com/iam/docs/creating-managing-service-account-keys) 
2. In the props object, replace the `service_account_json` value with the contents of the service account JSON file and set `service_account` to `true`.
3. Make sure that the service account in question has access to the folder specified in `root_folder_id`
4. Deploy

## Lite mode

This mode will serve a simple nginx-like directory listing, and it only work with one drive. `upload` will be ignored in this mode.

On the top of the script, change `lite: false` into `lite: true`, than thats all.

To enable on-the-fly lite mode, especially with command-line applications, you can include a HTTP header `x-lite: true` in your requests.

[Lite mode demo](https://gdindex-demo-lite.maple3142.workers.dev/)
