# webexcat

A simple way of sending messages from the CLI output to your Webex space with webhook.
> Actually, this is a fork version of [discat](https://github.com/dwisiswant0/discat) which is a fork of [slackcat](https://github.com/dwisiswant0/slackcat).

## Installation

- Download a prebuilt binary from [releases page](https://github.com/eforbus/webexcat/releases/latest), unpack and run! or
- If you have go1.13+ compiler installed: `go get github.com/eforbus/webexcat`.

## Configuration

**Step 1:** Get your Webex space webhook URL [here](https://apphub.webex.com/messaging/applications/incoming-webhooks-cisco-systems-38054)

**Step 2** _(optional)_**:** Set `WEBEX_WEBHOOK_URL` environment variable.
```bash
export WEBEX_WEBHOOK_URL="https://webexapis.com/v1/webhooks/incoming/XXX"
```

## Usage

It's very simple!

```bash
▶ echo -e "Hello,\nworld!" | webexcat
```

### Flags

```
Usage of webexcat:
  -1    Send message line-by-line
  -u string
        Webex Webhook URL
  -v    Verbose mode
```

### Workaround

The goal is to get automated alerts for interesting stuff!

```bash
▶ assetfinder twitter.com | anew | webexcat -u https://webexapis.com/v1/webhooks/incoming/XXX
```

The `-u` flag is optional if you've defined `WEBEX_WEBHOOK_URL` environment variable.

webexcat also strips the ANSI colors from stdin to send messages, so you'll receive a clean message on your space!

```bash
▶ nuclei -l urls.txt -t cves/ | webexcat
```

### Line-by-line

Instead of have to wait for previously executed program to finish, use the `-1` flag if you want to send messages on a line by line _(default: false)_.

```bash
▶ amass track -d domain.tld | webexcat -1
```

## License

`webexcat` is distributed under MIT License.
