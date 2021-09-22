Route53 is a managed DNS

A: Hostname => ipv4
AAAA: Hostname => IPv6
CNAME: Hostname => hostname
Alias: Hostname to AWS Resource (can be used with root domain) Free pointing to aws resources
	used for directing traffic to load balancers


Domain Names can be purchased through amazon for ~12/yr or transfered

Dns troubleshooting can be done with `dig` and `nslookup`

DNS Records Time to Live (TTL)

High TTL - 24 hours (less traffic on dns) Records maybe outdated
Low TTL - 60 seconds More DNS queries, less chance records outdated

Dig will give you the remaining TTL from cache
