# use-application-dns.net

## What is this domain?

This domain is intended to be a content-neutral name that DNS filtering products add to their domain block lists.

This will allow users, as well as browsers and other user agents that may implement DNS themselves, to know that the default DNS has implemented some sort of content policy that the user may wish to maintain, and thus application DNS perhaps should not be used, since it would bypass that policy.

## How to use this

Resolve use-application-dns.net using the platform's DNS. If the result is NXDOMAIN, then there is some sort of content filtering or other policy implemented by platform DNS. If the domain returns a result, then there is not (or the DNS server has not added use-application-dns.net to its filtering lists.)

Instructions for network administrators can be found [here](nxdomain-instructions.md).

## Who runs this?

This domain is run by [Mozilla](https://mozilla.org), as an interim measure while an RFC is pursured through the IETF.
