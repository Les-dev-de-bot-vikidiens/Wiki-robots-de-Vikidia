# Myrinet - Wikipedia

{% hint style="warning" %}
This article needs additional citations for [verification](/broken/pages/bf9a4056b0251e7f593c67472b783884014cb97b). Please help improve this article by [adding citations to reliable sources](/broken/pages/11488ed8dd7aaaef5853a9fd1b9f0a7c37c46441). Unsourced material may be challenged and removed.
{% endhint %}

## Myrinet

Myrinet, ANSI/VITA 26-1998, is a high-speed [local area networking](/broken/pages/fd7dc0d81d804d040b5b8fbd966c47e3a74af47d) system designed by the company Myricom to be used as an interconnect between multiple machines to form [computer clusters](/broken/pages/a2b7577753b8d17e43a44c49aafd1f6b36983e43).

### Description

Myrinet was promoted as having lower protocol overhead than standards such as [Ethernet](/broken/pages/d6785ac61a8dfa5f38f07cb551594c4d47ca637e), and therefore better [throughput](/broken/pages/049374031f772f79e882b71cfb3717c9a0af3925), less interference, and lower [latency](/broken/pages/faec70ede3f09ad31cfef57a1cb0e57fe036a3d9) while using the host CPU. Although it can be used as a traditional networking system, Myrinet is often used directly by programs that "know" about it, thereby bypassing a call into the [operating system](/broken/pages/bbb3cf2d62b6eadb5d7bc55b8038c29cd689f14f).

Earlier versions of Myrinet used a variety of media and connectors:[\[1\]](myrinet-wikipedia.md#cite_note-1)

* Generation 2 used copper media with [DC-37](/broken/pages/fc7cc3d7071cd6bbdb403e5ef0dfe54b1f759257) (Myrinet-LAN, M2L-\* controllers and switches) or microribbon (Myrinet-SAN, M2M-\*) connectors.
* Generation 3 used copper media with HSSDC (Myrinet-Serial, M3S-_) or microribbon (Myrinet-SAN, M3M-_) connectors, or fiber with LC-connectors (Myrinet-Fiber, M3F-\*).

The later versions of Myrinet physically consist of two [fibre optic](/broken/pages/a2e5bf76cfb31266304e992cfb51fc74824405da) cables, upstream and downstream, connected to the host computers with a single connector. Machines are connected via low-overhead [routers](/broken/pages/e563fdee898a329ca25d933c3800b17db2b44d57) and [switches](/broken/pages/f9300afbc05086dd6668f24ce16d20a0a7422f2b), as opposed to connecting one machine directly to another. Myrinet includes a number of fault-tolerance features, mostly backed by the switches. These include flow control, error control, and "heartbeat" monitoring on every link. The "fourth-generation" Myrinet, called Myri-10G, supported a 10 Gbit/s data rate and can use [10 Gigabit Ethernet](/broken/pages/bc03838525914dc404cdf1987801ae471977a131) on [PHY](/broken/pages/869cad6a4e6cb248e86d7856da49c76920a356a2), the physical layer (cables, connectors, distances, signaling). Myri-10G started shipping at the end of 2005.

Myrinet was approved in 1998 by the [American National Standards Institute](/broken/pages/a96745d8ea0b4a9e404325b8451f3e520e09fa13) for use on the [VMEbus](/broken/pages/479b70667dfc959609192a8ba9b84c2d14e7b97b) as ANSI/VITA 26-1998.[\[2\]](myrinet-wikipedia.md#cite_note-2) One of the earliest publications on Myrinet is a 1995 IEEE article.[\[3\]](myrinet-wikipedia.md#cite_note-3)

### Performance

| Generation | Year[\[4\]](myrinet-wikipedia.md#cite_note-4) | Bandwidth | Notes                                                                                           |
| ---------- | --------------------------------------------- | --------- | ----------------------------------------------------------------------------------------------- |
| 1          | Myrinet                                       | 1994      | 0.64 Gbit/s                                                                                     |
| 2          | Myrinet-LAN                                   | 1996      | 1.28 Gbit/s                                                                                     |
|            | Myrinet-SAN                                   |           | System-Area Network, shorter reach (3m) but lower cost[\[6\]](myrinet-wikipedia.md#cite_note-6) |
| 3          | Myrinet-2000                                  | 2000      | 2 Gbit/s                                                                                        |
| 4          | Myri-10G                                      | 2005      | 10 Gbit/s                                                                                       |

Myrinet is a lightweight protocol with little overhead that allows it to operate with throughput close to the basic signaling speed of the physical layer. For supercomputing, the low latency of Myrinet is even more important than its throughput performance, since, according to [Amdahl's law](/broken/pages/4aa9725cbda1e9424fb0880f3284c63ec4440568), a high-performance parallel system tends to be bottlenecked by its slowest sequential process, which in all but the most [embarrassingly parallel](/broken/pages/178263fb857c9144fedfda4a74c17341869bf036) supercomputer workloads is often the latency of message transmission across the network.

### Deployment

According to Myricom, 141 (28.2%) of the June 2005 [TOP500](/broken/pages/a83da091498cbd9adedd09248d5fda3219523637) supercomputers used Myrinet technology. In the November 2005 TOP500, the number of supercomputers using Myrinet was down to 101 computers, or 20.2%, in November 2006, 79 (15.8%), and by November 2007, 18 (3.6%), a long way behind [gigabit Ethernet](/broken/pages/029ae764978cb53972ee255669aacbb4f07d1285) at 54% and [InfiniBand](/broken/pages/1c26612fa25e9feb937855de46f582f6f9b82af7) at 24.2%.

In the June 2014 TOP500 list, the number of supercomputers using Myrinet interconnect was 1 (0.2%).[\[7\]](myrinet-wikipedia.md#cite_note-7)[\[8\]](myrinet-wikipedia.md#cite_note-8)

In November, 2013, the assets of Myricom (including the Myrinet technology) were acquired by CSP Inc.[\[9\]](myrinet-wikipedia.md#cite_note-9) In 2016, it was reported that [Google](/broken/pages/453cf7c17089dc9f05efe889c2fba5572a7eaecc) had also offered to buy the company.[\[10\]](myrinet-wikipedia.md#cite_note-10)

### See also

* [HIPPI](/broken/pages/ca8fd62b825f689dd6e860440b87e2aa69876000)
* [InfiniBand](/broken/pages/1c26612fa25e9feb937855de46f582f6f9b82af7)
* [List of device bandwidths](/broken/pages/f60bb538210aeb10131e38f21d9a36ee9a7c6cc5)
* [NUMAlink](/broken/pages/a47e168133b386628646c7c5af687b04910f5f1d)
* [Quadrics (company)](/broken/pages/06498b40d7a7de195558026589aee0db2c022eef)
* [RapidIO](/broken/pages/20fc27468ef46070558fa160099cc28ee7c943b6)
* [Scalable Coherent Interconnect](/broken/pages/e4cdc84b763fe1972d7518c2ce8583cf1949902f) (SCI)

### References

1. Guide to Myrinet/PCI Host Interfaces, Myricom, Inc., 18 February 2002
2. _American National Standard for Myrinet-on-VME Protocol Specification_ (PDF). VMEbus International Trade Association. November 2, 1998. [ISBN 1-885731-15-9](/broken/pages/f3968ad8bc7282e7e333ecb858670de69c407c49). [Archived (PDF)](https://web.archive.org/web/20141111221726/https://ph-dep-ese.web.cern.ch/ph-dep-ese/crates/standards/Av26.pdf) from the original on November 11, 2014. Retrieved September 1, 2016.
3. Boden, N.J.; Cohen, D.; Felderman, R.E.; Kulawik, A.E.; Seitz, C.L.; Seizovic, J.N.; Wen-King Su (1995). "Myrinet: A gigabit-per-second local area network". _IEEE Micro_. 15: 29–36. doi:10.1109/40.342015.
4. Padua, David, ed. (2011). _Encyclopedia of Parallel Computing_. IEEE. pp. 1239–1247. doi:10.1007/978-0-387-09766-4. ISBN 978-0-387-09765-7.
5. "M2M-M2F description". 1997-01-17. Archived from the original on 1997-01-17. Retrieved 2023-11-11.
6. "Myrinet - A Brief, Technical Overview". 1997-01-17. Archived from the original on 1997-01-17. Retrieved 2023-11-11.
7. "List Statistics". Archived from the original on 2018-07-18. Retrieved 2014-01-13.
8. "Deployment Time Series Chart". Archived from the original on 2014-02-01. Retrieved 2014-01-16.
9. "CSP, Inc. Broadens MultiComputer Business Opportunities With Asset Purchase of Myricom, Inc". Press Release. November 6, 2013. Archived from the original on September 11, 2016. Retrieved September 1, 2016.
10. Chris Williams (February 9, 2016). "Google crafts custom networking CPU with parallel computing links". _The Register_. Archived from the original on August 11, 2016. Retrieved September 1, 2016.

### External links

* [Myrinet site](https://web.archive.org/web/20130816035225/http://www.myricom.com/) at the [Wayback Machine](/broken/pages/4d573de5797b8daae0f21a96156079565b27d5e5) (archived August 16, 2013)
* [CSPI](http://www.cspi.com/), current owner of Myrinet.
