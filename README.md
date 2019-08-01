## Prerequisite

- DD-WRT firmware
- dnsmasq enabled
- ss-tunnel/ss-redir installed (For example installed from Entware)

## Install

1. Copy the repo to somewhere `</path/to/ss>`
2. Add dnsmasq configure: `conf-dir=</path/to/ss>/dnsmasq.d`
3. Edit `param.env` to fill your shadowsocks' server host and port (`SS_SERVER_HOST/SS_SERVER_PORT`)
4. Optionally changes `ss-tunnel` or `ss-redir` local port (`SS_TUNNEL_LOCAL_PORT`/`SS_REDIR_LOCAL_PORT`)
5. Edit `shadowsocks.json` to fill password and encrypt method
6. Run `run-ss-dnsmasq`/`run-ss-iptables`/`run-ss-tunnel`/`run-ss-redir` `start|stop` inside `</path/to/ss>`

## How it works

`ss-tunnel` is mainly used for DNS and `ss-redir` as transparent proxy.

`dnsmasq.d` contains configurations to decide which domains are using direct DNS (114.114.114.114), otherwise `ss-tunnel`.

If the resolved ip is an [APNIC](https://www.apnic.net/) ip, then connect to it directly, otherwise `ss-redir`. This is done by some iptables rules.

## Credit/Reference

- https://github.com/Entware/Entware/wiki/Alternative-install-vs-standard
- https://github.com/Entware/Entware/wiki/How-to-add-a-new-package
- https://github.com/softwaredownload/openwrt-fanqiang
- https://www.awsomejiang.com/2018/08/10/Tomato-with-shadowsocks-libev-Automatic-proxy-for-your-router/
- https://www.iana.org/assignments/ipv4-address-space/ipv4-address-space.xhtml
- https://www.apnic.net/manage-ip/manage-resources/address-status/apnic-resource-range/
