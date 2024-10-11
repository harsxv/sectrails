# sectrails

This script allows you to interact with the [SecurityTrails API](https://securitytrails.com/corp/api) to fetch domain details and DNS history. It provides two main commands: one for retrieving domain details and another for fetching DNS history.

## Setup

To use this script, you need an API key from SecurityTrails. You can obtain the API key by signing up for an account on [SecurityTrails](https://securitytrails.com/corp/api).

Once you have your API key, export it as an environment variable:

```bash
export SECTRAILS_API_KEY="your_api_key_here"
```

## Usage

```bash
$ sectrails
Usage: sectrails <command> <domain>
Commands:
  --info      Get details of a domain
  --history   Get DNS history of a domain
```

### Available Commands

- `--info`: Fetch domain details, including A, MX, NS, SOA, and TXT records.
- `--history`: Fetch DNS history for a domain.

### Examples

#### Get Domain Information

```bash
sectrails --info harry.id

=== Domain Details for harry.id ===

* Apex Domain: harry.id
* Hostname: harry.id
* Current DNS:

A Records:
* IP: 76.76.21.21 (First Seen: N/A, Organization: Amazon.com, Inc.)

MX Records:
* Hostname: route3.mx.cloudflare.net (Priority: 32, First Seen: N/A, Organization: Cloudflare, Inc.)
* Hostname: route2.mx.cloudflare.net (Priority: 5, First Seen: N/A, Organization: Cloudflare, Inc.)
* Hostname: route1.mx.cloudflare.net (Priority: 7, First Seen: N/A, Organization: Cloudflare, Inc.)

NS Records:
* Nameserver: robin.ns.cloudflare.com (First Seen: N/A, Organization: Cloudflare, Inc.)
* Nameserver: adam.ns.cloudflare.com (First Seen: N/A, Organization: Cloudflare, Inc.)

SOA Record:
* Email: dns.cloudflare.com (TTL: 10000)

TXT Records:
* Value: v=spf1 include:_spf.mx.cloudflare.net include:_spf.google.com ~all
* Value: google-site-verification=4YQjBgagAGO9b4AY-4HSqcOdR76OK_ObzgwlREdKN6U
```

This command retrieves and displays the following information about the domain:
- Apex Domain
- Hostname
- A Records (IP addresses and organization info)
- MX Records (mail exchange servers)
- NS Records (nameservers)
- SOA Records (start of authority)
- TXT Records (text records)

#### Get DNS History

```bash
sectrails --history harry.id

=== DNS History for harry.id ===

First Seen: 2024-05-25
Last Seen: 2024-10-11
Organizations: Amazon.com, Inc.
* IP Address: 76.76.21.21
-------------------------------
First Seen: 2024-02-16
Last Seen: 2024-05-25
Organizations: Cloudflare, Inc.
* IP Address: 104.21.28.251
-------------------------------
First Seen: 2024-02-16
Last Seen: 2024-05-25
Organizations: Cloudflare, Inc.
* IP Address: 172.67.147.238
-------------------------------
First Seen: 2023-12-29
Last Seen: 2024-02-16
Organizations: PT Deneva
* IP Address: 103.56.204.60
-------------------------------
First Seen: 2023-12-20
Last Seen: 2023-12-29
Organizations: PT Deneva
* IP Address: 103.56.204.49
-------------------------------
First Seen: 2023-11-26
Last Seen: 2023-12-20
Organizations: PT Deneva
* IP Address: 103.56.204.60
-------------------------------
First Seen: 2023-07-13
Last Seen: 2023-07-19
Organizations: Google LLC
* IP Address: 34.148.79.160
-------------------------------
First Seen: 2023-07-13
Last Seen: 2023-07-19
Organizations: Google LLC
* IP Address: 34.74.37.249
-------------------------------
First Seen: 2023-07-10
Last Seen: 2023-07-13
Organizations: Google LLC
* IP Address: 34.148.147.18
-------------------------------
First Seen: 2023-07-10
Last Seen: 2023-07-13
Organizations: Google LLC
* IP Address: 35.231.210.182
-------------------------------
First Seen: 2023-07-07
Last Seen: 2023-07-10
Organizations: Google LLC
* IP Address: 34.148.79.160
-------------------------------
First Seen: 2023-07-07
Last Seen: 2023-07-10
Organizations: Google LLC
* IP Address: 34.74.37.249
-------------------------------
First Seen: 2023-07-04
Last Seen: 2023-07-07
Organizations: Google LLC
* IP Address: 34.148.97.127
-------------------------------
First Seen: 2023-07-04
Last Seen: 2023-07-07
Organizations: Google LLC
* IP Address: 34.73.83.172
-------------------------------
First Seen: 2023-07-01
Last Seen: 2023-07-04
Organizations: Google LLC
* IP Address: 34.148.147.18
-------------------------------
First Seen: 2023-07-01
Last Seen: 2023-07-04
Organizations: Google LLC
* IP Address: 34.74.37.249
-------------------------------
First Seen: 2023-06-27
Last Seen: 2023-07-01
Organizations: Google LLC, Amazon.com, Inc.
* IP Address: 34.74.170.74
-------------------------------
First Seen: 2023-06-27
Last Seen: 2023-07-01
Organizations: Google LLC, Amazon.com, Inc.
* IP Address: 54.161.234.33
-------------------------------
First Seen: 2023-06-24
Last Seen: 2023-06-27
Organizations: Amazon.com, Inc., Google LLC
* IP Address: 18.213.222.111
-------------------------------
First Seen: 2023-06-24
Last Seen: 2023-06-27
Organizations: Amazon.com, Inc., Google LLC
* IP Address: 35.229.48.116
-------------------------------
First Seen: 2023-06-21
Last Seen: 2023-06-24
Organizations: Amazon.com, Inc.
* IP Address: 54.161.234.33
-------------------------------
First Seen: 2023-06-21
Last Seen: 2023-06-24
Organizations: Amazon.com, Inc.
* IP Address: 54.84.236.175
-------------------------------
First Seen: 2023-01-18
Last Seen: 2023-03-02
Organizations: Contabo Asia Private Limited
* IP Address: 109.123.237.99
-------------------------------
First Seen: 2022-10-05
Last Seen: 2022-11-13
Organizations: CV. Rumahweb Indonesia
* IP Address: 103.253.215.19
-------------------------------
First Seen: 2020-10-04
Last Seen: 2022-10-05
Organizations: OC1-SolarVPS, LLC
* IP Address: 181.214.31.165
-------------------------------
First Seen: 2017-12-26
Last Seen: 2020-10-03
Organizations: OC1-SolarVPS, LLC
* IP Address: 181.214.31.165
-------------------------------
First Seen: 2017-09-29
Last Seen: 2017-12-26
Organizations: Server Central Network
* IP Address: 205.234.136.4
-------------------------------
```

This command retrieves and displays the DNS A record history, including:
- First Seen Date
- Last Seen Date
- Organizations associated with the IP addresses
