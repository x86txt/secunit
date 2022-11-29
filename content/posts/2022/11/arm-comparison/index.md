---
title: "arm cpu comparison | secunit"
date: 2022-11-25T11:19:39-04:00
toc: false
images:
type: post
---

<p>Hi everyone - like many of you, I love the x86 vs arm race that is going on and actually use an M1 Max as my daily driver - with a 5950x + 3080 with 32GB of b-die as my backup/gaming machine - and so I'm always on the lookout for faster and more capable arm boards, or even full servers.</p>

Sadly, most arm servers are still *much* too expensive to use in my homelab, although the [Honeycomb LXS Server](https://www.servethehome.com/solidrun-honeycomb-lx2-server-announced-1u-2-node-arm/) is getting closer to reasonable prices ($3k for the server, $800 for just the board + cpu).

A friend of mine left Apple's processor division and went to work for Qualcomm and is holding out hope that the [Qualcomm Cloud AI 100](https://www.qualcomm.com/content/dam/qcomm-martech/dm-assets/documents/Prod-Brief-QCOM-Cloud-AI-100.pdf?fbclid=IwAR0pYyGkqA1sx7ukYb9Ctfq6yS7BJMSbQJlG5Ad0nPqry5_sf0l4mGfn3OE) will provide some competition in the server space and also believes that their desktop efforts will bear fruit. Their desktop effort are based on a company they acquired [Nuvia](https://www.extremetech.com/computing/337029-qualcomm-promises-its-new-cpus-will-aim-for-desktop-performance-leadership-but-may-not-ship-until-2024) and not 'yet another' re-purposed mobile chip. They claim we'll see silicon shipping in 2024, but we'll see.

I wrote all this today because I was interested to see how my 6-core ODroid-N2+ SBC (widely regarded as the faster ARM SBCs out) fared in Geekbench against my 10-core M1 Max - I know, not fair at all, but still interesting.

<small>(And yes, I know Geekbench is seethingly hated amongst professional reviewers, I'm sure [Hardware Jesus](https://www.youtube.com/user/gamersnexus) will forgive me this one time ...)</small>

So, without further adoo:

| Device | Single & Multi Core |
|--------|---------------|
|[O-Droid-N2+:](https://www.hardkernel.com/shop/odroid-n2-with-4gbyte-ram-2/) | [357, 1190](https://browser.geekbench.com/v5/cpu/18869787) |
| [M1 Max:](https://en.wikipedia.org/wiki/Apple_M1) | [1791, 12721](https://browser.geekbench.com/v5/cpu/18869739) |
| [Ryzen 9 5950X:](https://en.wikichip.org/wiki/amd/ryzen_9/5950x) | [1706, 17604](https://browser.geekbench.com/v5/cpu/17818166) |