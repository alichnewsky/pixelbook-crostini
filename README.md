# pixelbook-crostini

Notes, links and resources about running linux containers on a chromebook ( PixelBook ) using Crostini (i.e. ChromeOS' Linux applications support )

The intent is to collect here a journal of my various troubleshooting acts

## event logs

- 06/16/2019 : after last? chromeos update, could not launch my termina vm or penguin container, had to destroy it, and build a new one. See similar post [here](https://fedwiki.frankmcpherson.net/view/crostini-failure-after-chrome-os-74-upgrade). A potential mitigation measure on [Keith Myers' blog here](https://kmyers.me/blog/chromeos/chromeos-75-0-3759-4-rolling-out-to-the-dev-channel-backup-your-crostini-instance-before-rebooting-if-you-enable-the-gpu/).

```
> vmc start termina
Error: routine at frontends/vmc.rs:118 `vm_start(vm_name,user_id_hash,matches.opt_present("enable-gpu"))`
```
- 06/16/2019 : turned on `chrome://flags` for `#crostini-backup` `#crostini-usb-support` and `#crostini-app-search`


## working with multiple VM and containers

- can I launch a terminal for anything but the default `termina` vm and `penguin` stretch container
- docker inside `termina`, inside an `lxc` container... (this actually worked, I just never bothered documenting it)

## working with `docker` inside `termina` VM inside `penguin` container.
Instructions such as [these][(https://hackernoon.com/pixelbook-revisited-running-docker-containers-aa7c742a7dec) work out of the box...

The only trick seems to be to make sure you add your user to the `docker` group to get non-root access to the docker socket. That may require you to quit your container, stop/start your termina VM and launch `penguin` again. 

## Well known ports automatically forwarded from Chrome OS into the default `termina:penguin` container
source : [https://www.reddit.com/r/Crostini/wiki/index/well-known-ports](https://www.reddit.com/r/Crostini/wiki/index/well-known-ports)
```
3000,  // Rails
4200,  // Angular
5000,  // Flask
8000,  // Django
8008,  // HTTP alternative port
8080,  // HTTP alternative port
8085,  // Cloud SDK
8888,  // ipython/jupyter
9005,  // Firebase login
```
apparently the hostname `penguin.linux.test` points to it as well...

## automation
Backup / Restore etc.

## links
- [Chromium OS Docs - Running Custom Containers Under Chrome OS](https://chromium.googlesource.com/chromiumos/docs/+/master/containers_and_vms.md)
- [a closer look at chrome os, using LXD to run linux gui apps, project crostini](https://blog.simos.info/a-closer-look-at-chrome-os-using-lxd-to-run-linux-gui-apps-project-crostini/)
   - this contains a drill down of the difference between stock debian/stretch and google's crostini default image.
- [Keith Myers' blog](https://kmyers.me/knowledge/chromeos/)
- [Frank McPherson's wiki CrhomeOS section](https://fedwiki.frankmcpherson.net/view/welcome-visitors/view/site-index/)
   - [Frank McPherson's wiki crostini section](https://fedwiki.frankmcpherson.net/view/welcome-visitors/view/site-index/view/crostini)
   - [docker in crostini](https://fedwiki.frankmcpherson.net/view/welcome-visitors/view/site-index/view/docker-in-crostini)
     - [experiments with docker in crostini](https://fedwiki.frankmcpherson.net/view/welcome-visitors/view/site-index/view/experiments-with-docker-on-pixelbook)
- [reddit's r/Crostini ](https://www.reddit.com/r/Crostini)
   - [Using LXD/LXC In Termina to Launch containers](https://www.reddit.com/r/Crostini/wiki/howto/uselxd)
   - [Boostrapping a container](https://www.reddit.com/r/Crostini/wiki/getstarted/bootstrapping-a-container)
   - [How to go fishing for a file in a backed up vm](https://www.reddit.com/r/Crostini/comments/aw9hy7/can_anybody_start_termina_with_todays_dev_update/)
   - [How to reset everything](https://www.reddit.com/r/Crostini/comments/8ddx2l/question_how_to_reset_everything/)
- [Image server for LXC and LXD](https://us.images.linuxcontainers.org/)
- [pixelbook revisited - running docker containers](https://hackernoon.com/pixelbook-revisited-running-docker-containers-aa7c742a7dec)
