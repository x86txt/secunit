---
title: "tailscale | secunit"
date: 2022-11-23T11:19:39-04:00
toc: false
images:
---

<p>
<a href="https://tailscale.com/"><img src="https://secunit.pages.dev/images/tailscale.png" position="left" style="width:100px;float:left;"></a>
Tailscale is a Wireguard-based, <a href="https://tailscale.com/kb/1123/zero-trust/">zero-trust</a> mesh network technology that I've turned into a pretty big fan of. It can punch holes through most NAT devices via the use of DERP (<i>Designated Encrypted Relay for Packets</i>) servers, of which I run a couple for public consumption. <a href="https://tailscale.com/kb/1118/custom-derp-servers/">Tailscale maintains several public servers as well</a>, but I've found they're generally extremely overloaded and very slow - 1Mbps-2Mbps at most.

I run two on different providers (Linode and Vultr) in Atlanta to fill out a pretty big gap in their default DERP coverage.
</p>

If you'd like to use them there are a couple of ways to enable them, I'll show you the easier 'click-ops' GUI way here, via the <a href="https://tailscale.com/kb/1118/custom-derp-servers/">Custom DERP Servers</a> section of the Tailscale docs.

* Log into your Tailscale Admin Panel and hit the ACL screen: https://login.tailscale.com/admin/acls
* Add a derpMap section -

>**Note**: you can either keep the existing DERP servers provided by Tailscale in use, or tell it to ONLY utilize the DERP relays you specify, I chose the latter. If you don't want to do that, just omit the ```OmitDefaultRegions": true,``` line in the JSON below:

   
   ```json
   	"derpMap": {
		"OmitDefaultRegions": true,
		"Regions": {
			"900": {
				"RegionID":   900,
				"RegionCode": "atl",
				"RegionName": "Atlanta",
				"Nodes": [
					{
						"Name":     "1a",
						"RegionID": 900,
						"HostName": "derp-atl-1a.secunit.io",
						"IPv4":     "155.138.175.80",
						"IPv6":     "2001:19f0:5401:1d5b:5400:04ff:fe38:0be6",
					},
					{
						"Name":     "1b",
						"RegionID": 900,
						"HostName": "derp-atl-1b.secunit.io",
						"IPv4":     "139.144.18.21",
						"IPv6":     "2600:3c02::f03c:93ff:fefa:587a",
					},
				],
			},
		},
    },

```

After entering this and making sure the online editor reports there are no syntax errors in your langage, click the Save button. I'm not sure how long it will tske for the policy to filter to your clients, but you can verify this by issuing a ```tailscale netcheck``` command:

You should see something like this, with only the DERP servers you specified present:  

```json
Report:
	* UDP: true
	* IPv4: yes, 139.144.18.2:36651
	* IPv6: yes, [2600:3c02::f03c:93ff:fefa:587a]:33242
	* MappingVariesByDestIP:
	* HairPinning: true
	* PortMapping:
	* Nearest DERP: Atlanta
	* DERP latency:
		- atl: 100µs   (Atlanta)
  ```

If you have any questions, https://reddit.com/r/tailscale is the best place to ask, so good luck!