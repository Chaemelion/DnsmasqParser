## Dnsmasq Parser

A rudimentary FortiSIEM parser for dnsmasq queries collected via syslog, reverse engineered and developed from other parsers by myself and a coworker in a moment of inspiration during our [SANS Institute](https://www.sans.org/) course [SEC530](https://www.sans.org/cyber-security-courses/defensible-security-architecture-and-engineering/). Feedback and pull requests are welcome. 

### What it parses:
___

- Queries
  - A Records
    - Assigns ```dnsQueryName```, ```destName``` and ```domainEntropy``` for domains not ending in ```.local```
  - PTR Records
    - Assigns ```dnsQueryIpAddr``` and ```ipVersion```
- Replies
- Forwards
- Cached Queries


### Integration Notes:
___

Some of the built-in FortiSIEM rules match DNS traffic events on the event type group "Permitted Common DNS" which can be found in the interface under Resources > Event Types > Regular Traffic > Permit Traffic > Permitted Commond DNS. Within this group, we have added our desired parser events ```DnsmasqQueryA``` and ```DnsmasqQueryPTR```. Any other future event types you wish to capture should be included here, too. Hopefully future FortiSIEM rules will begin to reference similar event groups rather than hardcoded event types, making custom rules and parsers more easily integrated. 



