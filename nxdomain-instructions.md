# How to implement NXDOMAIN results (for network administrators)

Different nameserver implementations require different configuration

## BIND

Please refer to the [Knowledge Base article](https://kb.isc.org/docs/using-response-policy-zones-to-disable-mozilla-doh-by-default).

## Knot Resolver

Add this snippet to the configuration:

```lua
policy.add(policy.suffix(policy.DENY, {todname('use-application-dns.net.')}))
```

## PowerDNS Recursor

Create a Lua script with this content:

```lua
local uadns = newDN('use-application-dns.net')
function preresolve(dq)
  if uadns == dq.qname then
    dq.rcode = pdns.NXDOMAIN
    return true
  end
  return false
end
```

And load it using the [lua-dns-script](https://doc.powerdns.com/recursor/settings.html#lua-dns-script) configuration option.

## Unbound

Add the following to the Unbound configuration:

```
local-zone: "use-application-dns.net." always_nxdomain
```
