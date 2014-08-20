---
layout: post
title: Changing Your Windows 8 Product Key
date: 2012-10-28 15:08:22
categories: walkthroughs
---

I just recently installed Windows 8 on my home computer. During the installation process, I was not asked to provide a product key. This led to me not being able to activate Windows after the installation process.

To resolve this, follow these steps:

* From the start screen, type `cmd`
* Right-click on `Command Prompt` and select `Run as Administrator`
* Execute the following command: `slmgr -upk`
* Press `Windows+C` to bring up the Charms window
* Select `Settings` and click `Change PC Settings`
* The `Activate Windows` tab will now ask you for your product key

I oddly enough had trouble finding this info, so I thought I'd share
