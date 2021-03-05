---
title: "Nmap"
description: "Nmap"
lead: "Nmap"
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

## Basic Scans  

### Top Ports

{{< btn-copy text="nmap --top-ports 200 [target ip]" >}}

```bash
nmap --top-ports 200 [target ip]
```  

### Top Ports & Service Versions

{{< btn-copy text="nmap -sV --top-ports 200 [target ip]" >}}

```bash
nmap -sV --top-ports 200 [target ip]
```  

### All Ports, Service Versions, OS 

{{< btn-copy text="nmap -sV -A -O -p- [target  ip]" >}}

```bash
nmap -sV -A -O -p- [target  ip]
```


