## What is VXLAN?

VXLAN (Virtual Extensible LAN) stretches a local network across long distances — 
so devices act like they are plugged into the same switch, even if they are in 
different data centers or cities.

### The Problem

- A normal VLAN supports only **4,096 networks** — not enough for large clouds.
- Regular Layer 2 traffic cannot cross routers easily.

### How It Works (Simple Analogy)

Think of company mail sent inside standard envelopes through the public post office. 
The post office does not care what is inside; it just delivers the envelope.

VXLAN does the same with network packets:
1. A switch (**VTEP**) wraps a local packet inside a normal **IP/UDP** envelope.
2. The packet travels across the existing IP network (**underlay**).
3. The remote switch unwraps it and delivers it to the destination.

The servers never know they left their local network.

### Key Terms

| Term | Meaning |
|------|---------|
| **VTEP** | The tunnel endpoint switch that wraps and unwraps packets. |
| **VNI** | Virtual Network ID. Different VNIs are isolated channels (like VLAN tags, but millions of them). |
| **Underlay** | The physical IP network that carries the tunneled traffic. |
| **Overlay** | The virtual network that lives inside the tunnels. |

### Why Use It

- **Millions of networks** — breaks the 4,096 VLAN limit.
- **VM mobility** — move virtual machines between servers without changing IP addresses.
- **Any IP transport** — works across routers, the internet, or MPLS.

### One-Sentence Summary

&gt; VXLAN packs local network traffic into regular IP packets so it can travel 
&gt; anywhere, turning many physical switches into one big virtual switch.
