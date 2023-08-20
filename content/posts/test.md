+++
title = "Systemd - start dopo mount di un volume"
date = "2023-08-20T15:39:07+02:00"
author = ""
authorTwitter = "" #do not include @
cover = ""
tags = ["docker", "linux"]
keywords = ["", ""]
description = ""
showFullContent = false
readingTime = false
hideComments = false
color = "" #color from the theme settings
+++

Sul mio server con OpenMediaVault mi sono ritrovato con il seguente problema: il volume in RAID 1 di BTRFS necessita di alcuni secondi per essere montato in /mnt.
I container Docker che utilizzo per avviare i vari servizi partono prima, con il risultato che si ritrovano con dei volumi vuoti.
E' necessario fare in modo che Docker avvii i container solo **dopo** che il volume è stato montato.

<!--more-->

1. Trovare il mount point del volume con `systemctl list-unit-files | grep ".mount"`
2. Modificare il file systemd di docker con `systemctl edit docker.service` aggiungendo

```
[Unit]
Requires=xxx.mount
After=xxx.mount
```
