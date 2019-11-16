# http-proxy-to-socks5

[简介](https://github.com/oyyd/http-proxy-to-socks/blob/master/READMECN.md)

hpts(http-proxy-to-socks) is a nodejs tool to convert SOCKS proxy into http proxy.

Many clients support setting up http proxy to speed up network requests and for sometimes only SOCKS proxy is available to you. SOCKS proxy supports TCP so that it's possible to convert those requests from http proxy into SOCKS protocol. In this way, you can still keep the goodness provided by your SOCKS proxy(e.g. encryption).

## Setup

```
npm install -g http-proxy-to-socks5
```

Make sure your nodejs version is greater than `4`.

## Usage

```
hpts -s 127.0.0.1:1080 -p 8080 -s localhost|google.com|microsoft.com
```

This will start a process listening on `8080` as a http proxy. It will convert http requests into socks requests and send them to port `1080`. Please make sure your socks service is available at the corresponding port.

Other options:

```
Options:

  -h, --help             output usage information
  -V, --version          output the version number
  -s, --socks [socks]    specify your socks proxy host, default: 127.0.0.1:1080
  -p, --port [port]      specify the listening port of http proxy server, default: 8080
  -c, --config [config]  read configs from file in json format
  -s, --skip [hostname1|hostname2] skip proxy for hostname1 and hostname2 and so on, default localhost|127.0.0.1
  --level [level]        log level, vals: info, error
```

You can specify a `json` config file with `-c`:

```json
{
  "socks": "127.0.0.1:1080",
  "port": 8080
}
```

## CONTRIBUTE

Please add more tests for corresponding features when you send a PR:

```
npm run test
```

## License

MIT
