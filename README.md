# homeserver
My take on a current mini pc based homeserver to use for Docker/Kubernetes hosting

I wanted to host personal finance software somewhere 'near' me and found [firefly-iii](https://firefly-iii.org/). Now I needed a suitable homeserver...


## Why not use a hoster?

I thought about just grabbing some virtual server and run my Docker containers on it. But then I saw the price tags - if you want some RAM (32 gigs), you really need to invest more then 20€. E.g. have a look at Hetzner https://www.hetzner.com/de/cloud where a 32GB machine (shared vCPUs!) start at 38€.

So in only ten month I would have already spend a budget of 380€ - which I could also spend for my own homeserver! Well I wanted to do that since a long time, but didn't find the time to actually do so. Why not start now?


## Thinclients seem to be THE go-to thing today

I remembered bookmarking a Video from c't 3003 https://www.youtube.com/watch?v=cB5n_cWJor8 and started there (German only). They recommended using Thinclients as a start for your homeserver instead of a classic NAS, because they are much cheaper and are available completely without rotating parts like fans or HDDs.

> I know, why not use a Raspberry 4 or 5? Well there are still known limitations due to the ARM architecture (e.g. parts of Nextcloud not beeing supported) and also a Raspberry together with all needed components like SD card, power adapter, housing etc is also around 120€! With only 8GB of RAM... and ARM... and...

The [Fujitsu Futro S740](https://www.ram-koenig.de/Fujitsu-Futro-S740-ThinClient-Intel-J4105-150GHz-4GB-16GB-SSD-Netzteil) for example is around 80€s as refurbished and [seemed a great starting point](https://www.heise.de/ratgeber/Gebrauchter-Mini-PC-fuer-70-Euro-Thin-Client-Fujitsu-Futro-S740-7485477.html). There's also another recommendation in [this c't 3003 video](https://www.youtube.com/watch?v=K10bMgX0qoc) with the Dell Wyse 5070 Thin Client with Celeron J4105, which is kind of comparable to the Fujitsu model, but available even cheaper at around 60€ already.

I really liked the idea of only spending 60€, but the 4GBs of RAM wouldn't make for a great starting point for my Docker or Kubernetes hosting I guess. Gearing those Celeron J4105 machines up isn't easy, because of quite old hardware standards - and especially the restriction for using only small factor SSDs with only 4cms instead of the usual M.2 SSDs double the size. More than 512GBs would be a great problem to find. Not really great if I perspectively also wanted to host our family photo library and more on the homeserver. So I needed a more up-to-date system!


## More up-to-date architecture, but no noise aka fanless

Searching for more capability I found [this reddit thread](https://www.reddit.com/r/HomeServer/comments/1c06m4w/thin_client_recommendations/) where people suggest opting for a [Lenovo ThinkCentre M910q Tiny](https://www.refurbed.de/p/lenovo-thinkcentre-m910q-tiny/71916b/), which brings in much more power with it's Intel Core i5-6500T and a much more modern architecture.  

I found that a really great choice and even more reddit threads that recommend the machine! You can even stuff 32gigs of RAM into it along with a big 2TB SSD (or 4TB if you can afford it ;) ). BUT there's [one thing to consider](https://www.refurbed.de/p/lenovo-thinkcentre-m910q-tiny/71916b/): The Thinkcentre sadly has a fan! So it's not completely silent - and since I wanted to setup my homeserver right near my internet router in the living room, I didn't want to have any noice!

> Then I found a [c't 3003 video](https://www.youtube.com/watch?v=OOHszBodhbc) again and got to know about the Intel N100. This little peace of home server powering CPU seems to really the thing to choose right now in the home server community. It only has a TDP of 6W but [enough power (like 10-20% more than a 65W Coffee Lake-S Core i3-9100!)](https://wccftech.com/intel-n100-quad-e-core-cpu-gaming-benchmarks-surface-6w-chip-with-xe-lp-igpu/) and also all modern connectivity and standards. Sounds like a great basis for my home server!


## In search for fanless Intel N100 mini pcs

The c't video described [a AliExpress fanless mini pc based on the Intel N100](https://de.aliexpress.com/item/1005004360072281.html) that starts at 141€ as a barebone. But as the video and the product reviews suggest, the small pc gets really really hot and I was unsure, if I should order a machine from a non big player risking my house to burn... 

So I searched for different machines with Intel N100. I found [this box from Zotac](https://www.mindfactory.de/product_info.php/Zotac-ZBOX-CI337NANO-N100-Intel-DDR5-HDMI-DP-passiv_1515007.html), which sadly had mixed reviews. The [Zotac Zbox Edge CI343](https://www.heise.de/tests/Luefterloser-Mini-PC-im-Test-Zotac-Zbox-Edge-CI343-mit-Intel-N100-9584768.html?seite=all) was also a hot candidate, but I didn't find a free review. There was [the Blackview MP80]([https://www.techstage.de/test/guenstiger-mini-pc-bietet-erstaunlich-viel-t-bao-n100-fuer-165-euro-im-test/8pdzclb](https://www.techstage.de/test/klein-praktisch-gut-mini-pc-blackview-mp80-fuer-200-euro-ueberrascht-im-test/eslw67h)), which should be not loud - but still has a fan running. I found [the Minix Z100](https://www.techstage.de/test/passiv-gekuehlter-mini-pc-minix-z100-im-test-lautlos-durchdacht-und-gut-fuer-259-euro/31s7gee) to make for a really great package, if you're okay with a maximum of 8/16GB of RAM + 256/512GB of SSD - or with throwing both out and inserting more, which would have blasted my budget of 380€ max.

It was when I found out about the [Asus Expertcenter PN42](https://www.techstage.de/test/luefterloser-mini-pc-mit-geringem-stromverbrauch-im-test-asus-expertcenter-pn42/m517x1s), which seemed to be a completely silent N100 powered mini pc with low Watts consumption. It is also build for 24/7 operation [according to the companies website](https://www.asus.com/de/displays-desktops/mini-pcs/pn-series/asus-expertcenter-pn42/), which is my intended use case. And - using the Crucial website - I found out that [the Asus box can handle 32GB of RAM](https://www.crucial.de/compatible-upgrade-for/asus/asus-expertcenter-pn42-(n100-n200)), although not officially supported (overRAMing). So I finally ordered the Asus Expertcenter PN42 bare bone (205€) together with Crucial 32GB DDR4-3200 CL22 RAM (56€) and a Crucial P3 Plus SSD 2TB M.2 2280 PCIe Gen4 NVMe (109€). This made for a total of 370€, which was exactly in my budget. Let's see how this thing will run, when all parts arrived and I build them up.



# Find a suitable Linux distro

My homeserver hardware has arrived and I now wanted to install my Manjaro distro I'm already used to. But wait: Aren't there more practical distros for a server?

Let's have a look onto my requirements:

* Want to host a Kubernetes cluster: All in all I'm a DevOps guy and don't have my own K8s running (except from Cloud resources)? This needs to be changed! So the distro should support K8s as a first class citizen
* Minimal configuration overhead and maybe even configurable without an extra display, keyboard and mouse
* Ease update process and wide variety of packages (I really love my desktop Manjaro for exactly that reason!).


## Let's have a look at specialized container OSses

https://www.spectrocloud.com/blog/k3os-alternatives-the-best-container-os-for-edge-kubernetes

CoreOS and K3OS seem to be dead, Bottlerocket by Amazon is more or less limited to the AWS services and isn't that easy to install on bare-metal.

There seems to be https://www.talos.dev - which is supported by the CNCF. It supports bare-metal/edge and removes all SSH and console access in favor of API management.

But Talos is also immutable, which is great for beeing used as a base for Kubernetes - but don't we also want to run some home theater software also on our home server? Plex or the like... Hmm, and this will make the need for an X-Server (or Wayland)... 

Maybe [I simply start with Manjaro (as my most comfortalbe distro) for the moment](https://www.reddit.com/r/kubernetes/comments/qvvq7a/what_is_the_best_linux_os_to_deploy_kubernetes/) - and switch to a specialized Container OS later.



# Links

https://www.notebookcheck.com/Bosgame-Mini-PC-im-Test-Preiswerter-Kleinst-PC-mit-Intel-N95-fuer-den-Office-Alltag.727669.0.html

https://www.notebookcheck.net/Review-The-Asus-ExpertCenter-PN42-barebone-has-been-given-a-frugal-Intel-N200-and-DDR4-RAM.790005.0.html 

https://www.notebookcheck.net/Acemagic-S1-mini-PC-review-A-small-and-economical-office-PC-with-an-Intel-N95-1-TB-of-mass-storage-and-a-display.767513.0.html
