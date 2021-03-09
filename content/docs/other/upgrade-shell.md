---
title: "Upgrade Shell"
description: "Upgrade Shell"
lead: "Upgrade Shell"
date: 2020-11-12T15:22:20+01:00
lastmod: 2020-11-12T15:22:20+01:00
draft: false
images: []
menu: 
  docs:
    parent: "other"
weight: 620
toc: true
---

Use the following one liners if you have a limited shell  

{{< btn-copy text="export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin" >}}

```bash
export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
```  

{{< btn-copy text="export TERM=xterm" >}}

```bash
export TERM=xterm
```  

{{< btn-copy text="export SHELL=bash" >}}

```bash
export SHELL=bash
```  


```bash
python -c 'import pty;pty.spawn("/bin/bash")'
```  


