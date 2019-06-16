# pixelbook-croostini

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


## automation
Backup / Restore etc.

## links
