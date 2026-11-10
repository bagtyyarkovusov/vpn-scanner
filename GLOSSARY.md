# VPN service management

The operator's control plane for their own VPN access and the access they issue to others: it provisions the servers, issues access to users and reports whether each route works from the network it is meant for. Mainland China is the first target network; other restricted networks are separate problems handled in the same repository.

## Language

### Network

**Node**:
A server we operate running Xray that authenticates Users and sends their traffic onward, either straight to the internet or through an Upstream.
_Avoid_: Exit, server, backend, VPS

**Upstream**:
A VLESS account bought from a third-party provider that a Node sends traffic through. It can be replaced without any User's link changing.
_Avoid_: Provider code, source, backend link, airport

**Relay**:
A server inside mainland China that accepts a user's connection and forwards it unchanged to one Node.
_Avoid_: Entry, transit, 中转, forwarder, hop

**Line**:
One connectable route a user sees as a single link: either a Node reached directly, or a Relay paired with a Node.
_Avoid_: Route, link, server, location

### Access

**User**:
A person the operator has granted access, identified on every Node by one UUID.
_Avoid_: Client, customer, account, member

**Plan**:
The traffic quota and duration a User is granted.
_Avoid_: Package, tier, tariff

**Subscription**:
The per-User URL that returns that User's current Lines as `vless://` links.
_Avoid_: Sub link, config URL, profile

### Proof

**Probe**:
A machine on a mainland network that connects through every Line on a schedule and records latency and throughput.
_Avoid_: Monitor, checker, scanner
