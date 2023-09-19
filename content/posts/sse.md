+++
title = "Server sent events - configurazione nginx"
date = "2023-09-19T09:46:38+02:00"
author = ""
authorTwitter = "" #do not include @
cover = ""
tags = ["nginx", "reverse", "proxy", "sse"]
keywords = ["", ""]
description = ""
showFullContent = false
readingTime = false
hideComments = false
color = "" #color from the theme settings
+++

Configurazione nginx per supporto a server sent events, copiato spudoratamente da [qui](https://gist.github.com/maiha/4d5a5ff840edf36ea37e3454f0077801) (poi mi sono documentato sui vari parametri).

<!--more-->

Configurazione nginx "finale" o comunque colui che fornisce effettivamente la risposta.

```
Content-Type: text/event-stream;
Cache-Control: no-cache;
X-Accel-Buffering: no;
```

Configurazione eventuale reverse proxy intermedio

```
proxy_http_version 1.1;
proxy_set_header Connection "";
```
