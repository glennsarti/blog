---
layout: post
title: "Setting Up Your Test-Kitchen"
author: steven.murawski@gmail.com
comments: true
categories: []
tags: []
---

## Setting Up

### Get ChefDK

The easiest way to get started with Test-Kitchen for testing DSC resources is to [install ChefDK](http://stevenmurawski.com/powershell/2015/06/want-the-latest-chefdk-on-windows/).

ChefDK (or the Chef Development Kit) has a bunch of bundled tools, including Test-Kitchen, and a Ruby installation to run it.

## A Few Extra Tools

### Where should we run our machines?

A few options:

- Vagrant
- OpenStack
- Rackspace
- EC2
- Digital Ocean
- CloudStack
- Hyper-V
- and more

Since we are looking to test Windows Server and Desired State Configuration, I'm going to focus on Vagrant and Hyper-V.

#### First - Vagrant

If you haven't tried it out yet, Vagrant makes it easy to stand up virtualized environments and is usually used in local development scenarios.

Vagrant can use a number of different virtualization providers, with some of the more common being VirtualBox, VMWare Fusion, and Hyper-V.  I'm not going to go through a full Vagrant tutorial here, head on over to the [Getting Started](https://docs.vagrantup.com/v2/getting-started/index.html) page.

Since Microsoft has legal hurdles in place regarding sharing/distributing OS images, you'll likely have to build your own base images. [Matt Wrock](https://twitter.com/mwrockx) has written several times about this - [Creating windows base images using Packer and BoxStarter](http://www.hurryupandwait.io/blog/creating-windows-base-images-for-virtualbox-and-hyper-v-using-packer-boxstarter-and-vagrant), [In search of a light weight windows vagrant box](http://www.hurryupandwait.io/blog/in-search-of-a-light-weight-windows-vagrant-box), and [Creating a Hyper-V Vagrant box from a VirtualBox vmdk or vdi image](http://www.hurryupandwait.io/blog/creating-a-hyper-v-vagrant-box-from-a-virtualbox-vmdk-or-vdi-image).

You can find publicly available images on [Hashicorp's Atlas site](https://atlas.hashicorp.com/boxes/search).

ChefDK ships with the vagrant plugin for Test-Kitchen, but we should check for an updated version (just in case).  From PowerShell:

```
chef gem install kitchen-vagrant
```

We'll also need to make sure the vagrant-winrm plugin.  From PowerShell:

```
vagrant plugin install vagrant-winrm
```

I use Vagrant when I'm on my Mac and don't have Hyper-V available.

#### Alternative - If Vagrant isn't Your Thing

When I am on Windows and have Hyper-V installed, I do love me some Hyper-V.

To get Test-Kitchen ready to talk with Hyper-V, we'll need the kitchen-hyperv gem.  We can install that from PowerShell:

```
chef gem install kitchen-hyperv
```

### Almost there

To start testing DSC resources, we'll need a few more things.

From PowerShell:

```
chef gem install kitchen-dsc
chef gem install kitchen-pester
```


