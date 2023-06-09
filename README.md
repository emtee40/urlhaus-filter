# Malicious URL Blocklist

- Formats
  - [URL-based](#url-based)
  - [Domain-based](#domain-based)
  - [Hosts-based](#hosts-based)
  - [Domain-based (AdGuard Home)](#domain-based-adguard-home)
  - [URL-based (AdGuard)](#url-based-adguard)
  - [URL-based (Vivaldi)](#url-based-vivaldi)
  - [Dnsmasq](#dnsmasq)
  - [BIND zone](#bind)
  - [RPZ](#response-policy-zone)
  - [Unbound](#unbound)
  - [dnscrypt-proxy](#dnscrypt-proxy)
  - [Tracking Protection List (IE)](#tracking-protection-list-ie)
  - [Snort2](#snort2)
  - [Snort3](#snort3)
  - [Suricata](#suricata)
  - [Splunk](#splunk)
- [Compressed version](#compressed-version)
- [Reporting issues](#issues)
- [Cloning](#cloning)
- [FAQ and Guides](#faq-and-guides)
- [CI Variables](#ci-variables)
- [License](#license)

A blocklist of malicious websites that are being used for malware distribution, based on the **Database dump (CSV)** of Abuse.ch [URLhaus](https://urlhaus.abuse.ch/). Blocklist is updated twice a day.

There are multiple formats available, refer to the appropriate section according to the program used:

- uBlock Origin (uBO) -> [URL-based](#url-based) section (recommended)
- Pi-hole -> [Domain-based](#domain-based) or [Hosts-based](#hosts-based) section
- AdGuard Home -> [Domain-based (AdGuard Home)](#domain-based-adguard-home) or [Hosts-based](#hosts-based) section
- AdGuard (browser extension) -> [URL-based (AdGuard)](#url-based-adguard)
- Vivaldi -> [URL-based (Vivaldi)](#url-based-vivaldi)
- [Hosts](#hosts-based)
- [Dnsmasq](#dnsmasq)
- BIND -> BIND [zone](#bind) or [RPZ](#response-policy-zone)
- [Unbound](#unbound)
- [dnscrypt-proxy](#dnscrypt-proxy)
- Internet Explorer -> [Tracking Protection List (IE)](#tracking-protection-list-ie)
- [Snort2](#snort2)
- [Snort3](#snort3)
- [Suricata](#suricata)
- [Splunk](#splunk)

For other programs, see [Compatibility](https://gitlab.com/malware-filter/malware-filter/wikis/compatibility) page in the wiki.

Check out my other filters:

- [phishing-filter](https://gitlab.com/malware-filter/phishing-filter)
- [pup-filter](https://gitlab.com/malware-filter/pup-filter)
- [tracking-filter](https://gitlab.com/malware-filter/tracking-filter)
- [vn-badsite-filter](https://gitlab.com/malware-filter/vn-badsite-filter)

## URL-based

Import the following URL into uBO to subscribe (includes online and **offline** malicious websites):

- https://malware-filter.gitlab.io/malware-filter/urlhaus-filter.txt

<details>
<summary>Mirrors</summary>

- https://curbengh.github.io/malware-filter/urlhaus-filter.txt
- https://curbengh.github.io/urlhaus-filter/urlhaus-filter.txt
- https://malware-filter.gitlab.io/urlhaus-filter/urlhaus-filter.txt
- https://malware-filter.pages.dev/urlhaus-filter.txt
- https://urlhaus-filter.pages.dev/urlhaus-filter.txt

</details>

<br />

Lite version (**online** links only):

_enabled by default in uBO >=[1.28.2](https://github.com/gorhill/uBlock/releases/tag/1.28.2)_

- https://malware-filter.gitlab.io/malware-filter/urlhaus-filter-online.txt

<details>
<summary>Mirrors</summary>

- https://curbengh.github.io/malware-filter/urlhaus-filter-online.txt
- https://curbengh.github.io/urlhaus-filter/urlhaus-filter-online.txt
- https://malware-filter.gitlab.io/urlhaus-filter/urlhaus-filter-online.txt
- https://malware-filter.pages.dev/urlhaus-filter-online.txt
- https://urlhaus-filter.pages.dev/urlhaus-filter-online.txt

</details>

**Note:** Lite version is 99% smaller by excluding offline urls. The status of urls is determined by the upstream Abuse.ch. However, the test is not 100% accurate and some malicious urls that are otherwise accessible may be missed. If bandwidth (9 MB/day) is not a constraint, I recommend the regular version; browser extensions may utilise [HTTP compression](https://developer.mozilla.org/en-US/docs/Web/HTTP/Compression) that can save 70% of bandwidth.

Regular version contains >260K filters, do note that uBO can [easily handle](https://github.com/uBlockOrigin/uBlock-issues/issues/338#issuecomment-452843669) 500K filters.

If you've installed the lite version but prefer to use the regular version, it's better to remove it beforehand. Having two versions at the same time won't cause any conflict issue, uBO can detect duplicate network filters and adjust accordingly, but it's a waste of your bandwidth.

**AdGuard Home** users should use [this blocklist](#domain-based-adguard-home).

## URL-based (AdGuard)

Import the following URL into AdGuard browser extensions to subscribe (includes online and **offline** malicious websites):

- https://malware-filter.gitlab.io/malware-filter/urlhaus-filter-ag.txt

<details>
<summary>Mirrors</summary>

- https://curbengh.github.io/malware-filter/urlhaus-filter-ag.txt
- https://curbengh.github.io/urlhaus-filter/urlhaus-filter-ag.txt
- https://malware-filter.gitlab.io/urlhaus-filter/urlhaus-filter-ag.txt
- https://malware-filter.pages.dev/urlhaus-filter-ag.txt
- https://urlhaus-filter.pages.dev/urlhaus-filter-ag.txt

</details>

<br />

Lite version (**online** links only):

- https://malware-filter.gitlab.io/malware-filter/urlhaus-filter-ag-online.txt

<details>
<summary>Mirrors</summary>

- https://curbengh.github.io/malware-filter/urlhaus-filter-ag-online.txt
- https://curbengh.github.io/urlhaus-filter/urlhaus-filter-ag-online.txt
- https://malware-filter.gitlab.io/urlhaus-filter/urlhaus-filter-ag-online.txt
- https://malware-filter.pages.dev/urlhaus-filter-ag-online.txt
- https://urlhaus-filter.pages.dev/urlhaus-filter-ag-online.txt

</details>

## URL-based (Vivaldi)

_Requires Vivaldi Desktop/Android 3.3+, blocking level must be at least "Block Trackers"_

Import the following URL into Vivaldi's **Tracker Blocking Sources** to subscribe (includes online and **offline** malicious websites):

- https://malware-filter.gitlab.io/malware-filter/urlhaus-filter-vivaldi.txt

<details>
<summary>Mirrors</summary>

- https://curbengh.github.io/malware-filter/urlhaus-filter-vivaldi.txt
- https://curbengh.github.io/urlhaus-filter/urlhaus-filter-vivaldi.txt
- https://malware-filter.gitlab.io/urlhaus-filter/urlhaus-filter-vivaldi.txt
- https://malware-filter.pages.dev/urlhaus-filter-vivaldi.txt
- https://urlhaus-filter.pages.dev/urlhaus-filter-vivaldi.txt

</details>

<br />

Lite version (**online** links only):

- https://malware-filter.gitlab.io/malware-filter/urlhaus-filter-vivaldi-online.txt

<details>
<summary>Mirrors</summary>

- https://curbengh.github.io/malware-filter/urlhaus-filter-vivaldi-online.txt
- https://curbengh.github.io/urlhaus-filter/urlhaus-filter-vivaldi-online.txt
- https://malware-filter.gitlab.io/urlhaus-filter/urlhaus-filter-vivaldi-online.txt
- https://malware-filter.pages.dev/urlhaus-filter-vivaldi-online.txt
- https://urlhaus-filter.pages.dev/urlhaus-filter-vivaldi-online.txt

</details>

## Domain-based

This blocklist includes domains and IP addresses.

- https://malware-filter.gitlab.io/malware-filter/urlhaus-filter-domains.txt

<details>
<summary>Mirrors</summary>

- https://curbengh.github.io/malware-filter/urlhaus-filter-domains.txt
- https://curbengh.github.io/urlhaus-filter/urlhaus-filter-domains.txt
- https://malware-filter.gitlab.io/urlhaus-filter/urlhaus-filter-domains.txt
- https://malware-filter.pages.dev/urlhaus-filter-domains.txt
- https://urlhaus-filter.pages.dev/urlhaus-filter-domains.txt

</details>

<br />
Lite version (online domains/IPs only):

- https://malware-filter.gitlab.io/malware-filter/urlhaus-filter-domains-online.txt

<details>
<summary>Mirrors</summary>

- https://curbengh.github.io/malware-filter/urlhaus-filter-domains-online.txt
- https://curbengh.github.io/urlhaus-filter/urlhaus-filter-domains-online.txt
- https://malware-filter.gitlab.io/urlhaus-filter/urlhaus-filter-domains-online.txt
- https://malware-filter.pages.dev/urlhaus-filter-domains-online.txt
- https://urlhaus-filter.pages.dev/urlhaus-filter-domains-online.txt

</details>

## Domain-based (AdGuard Home)

This AdGuard Home-compatible blocklist includes domains and IP addresses.

- https://malware-filter.gitlab.io/malware-filter/urlhaus-filter-agh.txt

<details>
<summary>Mirrors</summary>

- https://curbengh.github.io/malware-filter/urlhaus-filter-agh.txt
- https://curbengh.github.io/urlhaus-filter/urlhaus-filter-agh.txt
- https://malware-filter.gitlab.io/urlhaus-filter/urlhaus-filter-agh.txt
- https://malware-filter.pages.dev/urlhaus-filter-agh.txt
- https://urlhaus-filter.pages.dev/urlhaus-filter-agh.txt

</details>

<br />
Lite version (online domains/IPs only):

- https://malware-filter.gitlab.io/malware-filter/urlhaus-filter-agh-online.txt

<details>
<summary>Mirrors</summary>

- https://curbengh.github.io/malware-filter/urlhaus-filter-agh-online.txt
- https://curbengh.github.io/urlhaus-filter/urlhaus-filter-agh-online.txt
- https://malware-filter.gitlab.io/urlhaus-filter/urlhaus-filter-agh-online.txt
- https://malware-filter.pages.dev/urlhaus-filter-agh-online.txt
- https://urlhaus-filter.pages.dev/urlhaus-filter-agh-online.txt

</details>

## Hosts-based

This blocklist includes domains only.

- https://malware-filter.gitlab.io/malware-filter/urlhaus-filter-hosts.txt

<details>
<summary>Mirrors</summary>

- https://curbengh.github.io/malware-filter/urlhaus-filter-hosts.txt
- https://curbengh.github.io/urlhaus-filter/urlhaus-filter-hosts.txt
- https://malware-filter.gitlab.io/urlhaus-filter/urlhaus-filter-hosts.txt
- https://malware-filter.pages.dev/urlhaus-filter-hosts.txt
- https://urlhaus-filter.pages.dev/urlhaus-filter-hosts.txt

</details>

<br />
Lite version (online domains only):

- https://malware-filter.gitlab.io/malware-filter/urlhaus-filter-hosts-online.txt

<details>
<summary>Mirrors</summary>

- https://curbengh.github.io/malware-filter/urlhaus-filter-hosts-online.txt
- https://curbengh.github.io/urlhaus-filter/urlhaus-filter-hosts-online.txt
- https://malware-filter.gitlab.io/urlhaus-filter/urlhaus-filter-hosts-online.txt
- https://malware-filter.pages.dev/urlhaus-filter-hosts-online.txt
- https://urlhaus-filter.pages.dev/urlhaus-filter-hosts-online.txt

</details>

## Dnsmasq

This blocklist includes domains only.

Save the ruleset to "/usr/local/etc/dnsmasq/urlhaus-filter-dnsmasq.conf". Refer to this [guide](https://gitlab.com/malware-filter/malware-filter/wikis/update-filter) for auto-update.

Configure dnsmasq to use the blocklist:

`printf "\nconf-file=/usr/local/etc/dnsmasq/urlhaus-filter-dnsmasq.conf\n" >> /etc/dnsmasq.conf`

- https://malware-filter.gitlab.io/malware-filter/urlhaus-filter-dnsmasq.conf

<details>
<summary>Mirrors</summary>

- https://curbengh.github.io/malware-filter/urlhaus-filter-dnsmasq.conf
- https://curbengh.github.io/urlhaus-filter/urlhaus-filter-dnsmasq.conf
- https://malware-filter.gitlab.io/urlhaus-filter/urlhaus-filter-dnsmasq.conf
- https://malware-filter.pages.dev/urlhaus-filter-dnsmasq.conf
- https://urlhaus-filter.pages.dev/urlhaus-filter-dnsmasq.conf

</details>

<br />
Lite version (online domains only):

- https://malware-filter.gitlab.io/malware-filter/urlhaus-filter-dnsmasq-online.conf

<details>
<summary>Mirrors</summary>

- https://curbengh.github.io/malware-filter/urlhaus-filter-dnsmasq-online.conf
- https://curbengh.github.io/urlhaus-filter/urlhaus-filter-dnsmasq-online.conf
- https://malware-filter.gitlab.io/urlhaus-filter/urlhaus-filter-dnsmasq-online.conf
- https://malware-filter.pages.dev/urlhaus-filter-dnsmasq-online.conf
- https://urlhaus-filter.pages.dev/urlhaus-filter-dnsmasq-online.conf

</details>

## BIND

This blocklist includes domains only.

### Install

Save the ruleset to "/usr/local/etc/bind/urlhaus-filter-bind.conf". Refer to this [guide](https://gitlab.com/malware-filter/malware-filter/wikis/update-filter) for auto-update.

Configure BIND to use the blocklist:

`printf '\ninclude "/usr/local/etc/bind/urlhaus-filter-bind.conf";\n' >> /etc/bind/named.conf`

Add this to "/etc/bind/null.zone.file" (skip this step if the file already exists):

```
$TTL    86400   ; one day
@       IN      SOA     ns.nullzone.loc. ns.nullzone.loc. (
               2017102203
                    28800
                     7200
                   864000
                    86400 )
                NS      ns.nullzone.loc.
                A       0.0.0.0
@       IN      A       0.0.0.0
*       IN      A       0.0.0.0
```

Zone file is derived from [here](https://github.com/tomzuu/blacklist-named/blob/master/null.zone.file).

- https://malware-filter.gitlab.io/malware-filter/urlhaus-filter-bind.conf

<details>
<summary>Mirrors</summary>

- https://curbengh.github.io/malware-filter/urlhaus-filter-bind.conf
- https://curbengh.github.io/urlhaus-filter/urlhaus-filter-bind.conf
- https://malware-filter.gitlab.io/urlhaus-filter/urlhaus-filter-bind.conf
- https://malware-filter.pages.dev/urlhaus-filter-bind.conf
- https://urlhaus-filter.pages.dev/urlhaus-filter-bind.conf

</details>

<br />
Lite version (online domains only):

- https://malware-filter.gitlab.io/malware-filter/urlhaus-filter-bind-online.conf

<details>
<summary>Mirrors</summary>

- https://curbengh.github.io/malware-filter/urlhaus-filter-bind-online.conf
- https://curbengh.github.io/urlhaus-filter/urlhaus-filter-bind-online.conf
- https://malware-filter.gitlab.io/urlhaus-filter/urlhaus-filter-bind-online.conf
- https://malware-filter.pages.dev/urlhaus-filter-bind-online.conf
- https://urlhaus-filter.pages.dev/urlhaus-filter-bind-online.conf

</details>

## Response Policy Zone

This blocklist includes domains only.

- https://malware-filter.gitlab.io/malware-filter/urlhaus-filter-rpz.conf

<details>
<summary>Mirrors</summary>

- https://curbengh.github.io/malware-filter/urlhaus-filter-rpz.conf
- https://curbengh.github.io/urlhaus-filter/urlhaus-filter-rpz.conf
- https://malware-filter.gitlab.io/urlhaus-filter/urlhaus-filter-rpz.conf
- https://malware-filter.pages.dev/urlhaus-filter-rpz.conf
- https://urlhaus-filter.pages.dev/urlhaus-filter-rpz.conf

</details>

<br />
Lite version (online domains only):

- https://malware-filter.gitlab.io/malware-filter/urlhaus-filter-rpz-online.conf

<details>
<summary>Mirrors</summary>

- https://curbengh.github.io/malware-filter/urlhaus-filter-rpz-online.conf
- https://curbengh.github.io/urlhaus-filter/urlhaus-filter-rpz-online.conf
- https://malware-filter.gitlab.io/urlhaus-filter/urlhaus-filter-rpz-online.conf
- https://malware-filter.pages.dev/urlhaus-filter-rpz-online.conf
- https://urlhaus-filter.pages.dev/urlhaus-filter-rpz-online.conf

</details>

## Unbound

This blocklist includes domains only.

Save the rulesets to "/usr/local/etc/unbound/urlhaus-filter-unbound.conf". Refer to this [guide](https://gitlab.com/malware-filter/malware-filter/wikis/update-filter) for auto-update.

Configure Unbound to use the blocklist:

`printf '\n  include: "/usr/local/etc/unbound/urlhaus-filter-unbound.conf"\n' >> /etc/unbound/unbound.conf`

- https://malware-filter.gitlab.io/malware-filter/urlhaus-filter-unbound.conf

<details>
<summary>Mirrors</summary>

- https://curbengh.github.io/malware-filter/urlhaus-filter-unbound.conf
- https://curbengh.github.io/urlhaus-filter/urlhaus-filter-unbound.conf
- https://malware-filter.gitlab.io/urlhaus-filter/urlhaus-filter-unbound.conf
- https://malware-filter.pages.dev/urlhaus-filter-unbound.conf
- https://urlhaus-filter.pages.dev/urlhaus-filter-unbound.conf

</details>

<br />
Lite version (online domains only):

- https://malware-filter.gitlab.io/malware-filter/urlhaus-filter-unbound-online.conf

<details>
<summary>Mirrors</summary>

- https://curbengh.github.io/malware-filter/urlhaus-filter-unbound-online.conf
- https://curbengh.github.io/urlhaus-filter/urlhaus-filter-unbound-online.conf
- https://malware-filter.gitlab.io/urlhaus-filter/urlhaus-filter-unbound-online.conf
- https://malware-filter.pages.dev/urlhaus-filter-unbound-online.conf
- https://urlhaus-filter.pages.dev/urlhaus-filter-unbound-online.conf

</details>

## dnscrypt-proxy

Save the rulesets to "/etc/dnscrypt-proxy/". Refer to this [guide](https://gitlab.com/malware-filter/malware-filter/wikis/update-filter) for auto-update.

Configure dnscrypt-proxy to use the blocklist:

```diff
[blocked_names]
+  blocked_names_file = '/etc/dnscrypt-proxy/urlhaus-filter-dnscrypt-blocked-names.txt'

[blocked_ips]
+  blocked_ips_file = '/etc/dnscrypt-proxy/urlhaus-filter-dnscrypt-blocked-ips.txt'
```

- https://malware-filter.gitlab.io/malware-filter/urlhaus-filter-dnscrypt-blocked-names.txt
- https://malware-filter.gitlab.io/malware-filter/urlhaus-filter-dnscrypt-blocked-ips.txt

<details>
<summary>Mirrors</summary>

- https://curbengh.github.io/malware-filter/urlhaus-filter-dnscrypt-blocked-names.txt
- https://curbengh.github.io/urlhaus-filter/urlhaus-filter-dnscrypt-blocked-names.txt
- https://malware-filter.gitlab.io/urlhaus-filter/urlhaus-filter-dnscrypt-blocked-names.txt
- https://malware-filter.pages.dev/urlhaus-filter-dnscrypt-blocked-names.txt
- https://urlhaus-filter.pages.dev/urlhaus-filter-dnscrypt-blocked-names.txt

- https://curbengh.github.io/malware-filter/urlhaus-filter-dnscrypt-blocked-ips.txt
- https://curbengh.github.io/urlhaus-filter/urlhaus-filter-dnscrypt-blocked-ips.txt
- https://malware-filter.gitlab.io/urlhaus-filter/urlhaus-filter-dnscrypt-blocked-ips.txt
- https://malware-filter.pages.dev/urlhaus-filter-dnscrypt-blocked-ips.txt
- https://urlhaus-filter.pages.dev/urlhaus-filter-dnscrypt-blocked-ips.txt

</details>

<br />
Lite version (online domains only):

- https://malware-filter.gitlab.io/malware-filter/urlhaus-filter-dnscrypt-blocked-names-online.txt
- https://malware-filter.gitlab.io/malware-filter/urlhaus-filter-dnscrypt-blocked-ips-online.txt

<details>
<summary>Mirrors</summary>

- https://curbengh.github.io/malware-filter/urlhaus-filter-dnscrypt-blocked-names-online.txt
- https://curbengh.github.io/urlhaus-filter/urlhaus-filter-dnscrypt-blocked-names-online.txt
- https://malware-filter.gitlab.io/urlhaus-filter/urlhaus-filter-dnscrypt-blocked-names-online.txt
- https://malware-filter.pages.dev/urlhaus-filter-dnscrypt-blocked-names-online.txt
- https://urlhaus-filter.pages.dev/urlhaus-filter-dnscrypt-blocked-names-online.txt

- https://curbengh.github.io/malware-filter/urlhaus-filter-dnscrypt-blocked-ips-online.txt
- https://curbengh.github.io/urlhaus-filter/urlhaus-filter-dnscrypt-blocked-ips-online.txt
- https://malware-filter.gitlab.io/urlhaus-filter/urlhaus-filter-dnscrypt-blocked-ips-online.txt
- https://malware-filter.pages.dev/urlhaus-filter-dnscrypt-blocked-ips-online.txt
- https://urlhaus-filter.pages.dev/urlhaus-filter-dnscrypt-blocked-ips-online.txt

</details>

## Tracking Protection List (IE)

This blocklist includes domains only. Supported in Internet Explorer 9+.

- https://malware-filter.gitlab.io/malware-filter/urlhaus-filter.tpl

<details>
<summary>Mirrors</summary>

- https://curbengh.github.io/malware-filter/urlhaus-filter.tpl
- https://curbengh.github.io/urlhaus-filter/urlhaus-filter.tpl
- https://malware-filter.gitlab.io/urlhaus-filter/urlhaus-filter.tpl
- https://malware-filter.pages.dev/urlhaus-filter.tpl
- https://urlhaus-filter.pages.dev/urlhaus-filter.tpl

</details>

<br />
Lite version (online domains only):

- https://malware-filter.gitlab.io/malware-filter/urlhaus-filter-online.tpl

<details>
<summary>Mirrors</summary>

- https://curbengh.github.io/malware-filter/urlhaus-filter-online.tpl
- https://curbengh.github.io/urlhaus-filter/urlhaus-filter-online.tpl
- https://malware-filter.gitlab.io/urlhaus-filter/urlhaus-filter-online.tpl
- https://malware-filter.pages.dev/urlhaus-filter-online.tpl
- https://urlhaus-filter.pages.dev/urlhaus-filter-online.tpl

</details>

## Snort2

This ruleset includes online URLs only. Not compatible with [Snort3](#snort3). Save the ruleset to "/etc/snort/rules/urlhaus-filter-snort2-online.rules". Refer to this [guide](https://gitlab.com/malware-filter/malware-filter/wikis/update-filter) for auto-update.

Configure Snort to use the ruleset:

`printf "\ninclude \$RULE_PATH/urlhaus-filter-snort2-online.rules\n" >> /etc/snort/snort.conf`

- https://malware-filter.gitlab.io/malware-filter/urlhaus-filter-snort2-online.rules

<details>
<summary>Mirrors</summary>

- https://curbengh.github.io/malware-filter/urlhaus-filter-snort2-online.rules
- https://curbengh.github.io/urlhaus-filter/urlhaus-filter-snort2-online.rules
- https://malware-filter.gitlab.io/urlhaus-filter/urlhaus-filter-snort2-online.rules
- https://malware-filter.pages.dev/urlhaus-filter-snort2-online.rules
- https://urlhaus-filter.pages.dev/urlhaus-filter-snort2-online.rules

</details>

## Snort3

This ruleset includes online URLs only. Not compatible with [Snort2](#snort2).

Save the ruleset to "/etc/snort/rules/urlhaus-filter-snort3-online.rules". Refer to this [guide](https://gitlab.com/malware-filter/malware-filter/wikis/update-filter) for auto-update.

Configure Snort to use the ruleset:

```diff
# /etc/snort/snort.lua
ips =
{
  variables = default_variables,
+  include = 'rules/urlhaus-filter-snort3-online.rules'
}
```

- https://malware-filter.gitlab.io/malware-filter/urlhaus-filter-snort3-online.rules

<details>
<summary>Mirrors</summary>

- https://curbengh.github.io/malware-filter/urlhaus-filter-snort3-online.rules
- https://curbengh.github.io/urlhaus-filter/urlhaus-filter-snort3-online.rules
- https://malware-filter.gitlab.io/urlhaus-filter/urlhaus-filter-snort3-online.rules
- https://malware-filter.pages.dev/urlhaus-filter-snort3-online.rules
- https://urlhaus-filter.pages.dev/urlhaus-filter-snort3-online.rules

</details>

## Suricata

This ruleset includes online URLs only.

Save the ruleset to "/etc/suricata/rules/urlhaus-filter-suricata-online.rules". Refer to this [guide](https://gitlab.com/malware-filter/malware-filter/wikis/update-filter) for auto-update.

Configure Suricata to use the ruleset:

```diff
# /etc/suricata/suricata.yaml
rule-files:
  - local.rules
+  - urlhaus-filter-suricata-online.rules
```

- https://malware-filter.gitlab.io/malware-filter/urlhaus-filter-suricata-online.rules

<details>
<summary>Mirrors</summary>

- https://curbengh.github.io/malware-filter/urlhaus-filter-suricata-online.rules
- https://curbengh.github.io/urlhaus-filter/urlhaus-filter-suricata-online.rules
- https://malware-filter.gitlab.io/urlhaus-filter/urlhaus-filter-suricata-online.rules
- https://malware-filter.pages.dev/urlhaus-filter-suricata-online.rules
- https://urlhaus-filter.pages.dev/urlhaus-filter-suricata-online.rules

</details>

## Splunk

A CSV file for Splunk [lookup](https://docs.splunk.com/Documentation/Splunk/9.0.2/Knowledge/Aboutlookupsandfieldactions). This ruleset includes online URLs only.

Either upload the file via GUI or save the file in `$SPLUNK_HOME/Splunk/etc/system/lookups` or app-specific `$SPLUNK_HOME/etc/YourApp/apps/search/lookups`. Refer to this [guide](https://gitlab.com/malware-filter/malware-filter/wikis/update-filter) or [Getwatchlist](https://splunkbase.splunk.com/app/635) app for auto-update.

Columns:

| host         | path       | message                                   | updated              |
| ------------ | ---------- | ----------------------------------------- | -------------------- |
| example.com  |            | urlhaus-filter malicious website detected | 2022-12-21T12:34:56Z |
| example2.com | /some-path | urlhaus-filter malicious website detected | 2022-12-21T12:34:56Z |

- https://malware-filter.gitlab.io/malware-filter/urlhaus-filter-splunk-online.csv

<details>
<summary>Mirrors</summary>

- https://curbengh.github.io/malware-filter/urlhaus-filter-splunk-online.csv
- https://curbengh.github.io/urlhaus-filter/urlhaus-filter-splunk-online.csv
- https://malware-filter.gitlab.io/urlhaus-filter/urlhaus-filter-splunk-online.csv
- https://malware-filter.pages.dev/urlhaus-filter-splunk-online.csv
- https://urlhaus-filter.pages.dev/urlhaus-filter-splunk-online.csv

</details>

## Third-party mirrors

<details>
<summary>iosprivacy/urlhaus-filter-mirror</summary>

TBC

</details>

## Compressed version

All filters are also available as gzip- and brotli-compressed.

- Gzip: https://malware-filter.gitlab.io/malware-filter/urlhaus-filter.txt.gz
- Brotli: https://malware-filter.gitlab.io/malware-filter/urlhaus-filter.txt.br

## Issues

This blocklist operates by blocking the **whole** website, instead of specific webpages; exceptions are made on popular websites (e.g. `https://docs.google.com/`), in which webpages are specified instead (e.g. `https://docs.google.com/malware-page`). Malicious webpages are only listed in the [URL-based](#url-based) filter, popular websites are excluded from other filters.

_Popular_ websites are as listed in the [Umbrella Popularity List](https://s3-us-west-1.amazonaws.com/umbrella-static/index.html) (top 1M domains + subdomains), [Tranco List](https://tranco-list.eu/) (top 1M domains), [Cloudflare Radar](https://developers.cloudflare.com/radar/investigate/domain-ranking-datasets/) (top 1M domains) and this [custom list](src/exclude.txt).

If you wish to exclude certain website(s) that you believe is sufficiently well-known, please create an [issue](https://gitlab.com/malware-filter/urlhaus-filter/issues) or [merge request](https://gitlab.com/malware-filter/urlhaus-filter/merge_requests). If the website is quite obscure but you still want to visit it, you can add a new line `||legitsite.com^$badfilter` to "My filters" tab of uBO; use a subdomain if relevant, `||sub.legitsite.com^$badfilter`.

This filter **only** accepts new malware URLs from [URLhaus](https://urlhaus.abuse.ch/).

Please report new malware URL to the upstream maintainer through https://urlhaus.abuse.ch/api/#submit.

## Cloning

Since the filter is updated frequently, cloning the repo would become slower over time as the revision grows.

Use shallow clone to get the recent revisions only. Getting the last five revisions should be sufficient for a valid MR.

`git clone --depth 5 https://gitlab.com/malware-filter/urlhaus-filter.git`

## FAQ and Guides

See [wiki](https://gitlab.com/malware-filter/malware-filter/-/wikis/home)

## CI Variables

Optional variables:

- `CLOUDFLARE_BUILD_HOOK`: Deploy to Cloudflare Pages.
- `NETLIFY_SITE_ID`: Deploy to Netlify.
- `CF_API`: Include Cloudflare Radar [domains ranking](https://developers.cloudflare.com/radar/investigate/domain-ranking-datasets/). [Guide](https://developers.cloudflare.com/radar/get-started/first-request/) to create an API token.

## License

[Creative Commons Zero v1.0 Universal](LICENSE-CC0.md) and [MIT License](LICENSE)

[URLhaus](https://urlhaus.abuse.ch/): [CC0](https://creativecommons.org/publicdomain/zero/1.0/)

[Tranco List](https://tranco-list.eu/): [MIT License](https://choosealicense.com/licenses/mit/)

[Umbrella Popularity List](https://s3-us-west-1.amazonaws.com/umbrella-static/index.html): Available free of charge by Cisco Umbrella

[Cloudflare Radar](https://developers.cloudflare.com/radar/investigate/domain-ranking-datasets/): Available to free Cloudflare account

This repository is not endorsed by Abuse.ch.
