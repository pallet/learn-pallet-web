---
layout: post
title: Setting up Learn Pallet
categories: getting-started
---

<p class="lead">Before you can run any of the code in the exercises, you need to setup
your computer to run Pallet. This document explains how to setup your
Pallet environment.</p>

The steps to setup your environment are: 
    
1. Make sure your computer complies with the prerequisites
2. Choose the infrastructure provider (Amazon AWS or VirtualBox) to
   use
3. Prepare your environment for your choice of infrastructure.

## Prerequisites

`learn-pallet` requires that you have the following installed on your
computer:

  - [A modern Java SDK][java] (Java 7 is recommended)
  - [Leiningen][lein] -- this is Clojure's favorite built tool. Use
    [this link][lein-win] for Windows. 
  - A SSH key-pair, located in a subdirectory of your home directory
    named `.ssh`. The keys should be named `id_rsa` and `id_rsa.pub`.
    GitHub has a [nice article][gen-ssh-keys] on how to go about
    generating these keys.

## Choose Target Infrastructure Provider

Pallet can target multiple infrastructure providers where it will
create and configure your infrastructure projects. Pallet will use any
(decently known) cloud provider, local virtual machines, or even your
own servers, and is up to you to decide which one.

For simplicity `learn-pallet` is pre-configured to run on Amazon's
public cloud and VirtualBox.

The easier provider to set-up is Amazon AWS, even more so if you
already have an account there. If you just want to play with Pallet
for a while or you don't care about the cost of running in a public
cloud, this is probably the way to go as there is no much setup to be
done. Also, if your machine is running Windows, this is the only
option that we currently support.

In case don't want to pay Amazon, you want to speed up your Pallet
runs, or you simply don't want to use a public cloud, there is also
the option to run Pallet locally on VirtualBox VMs. Pallet uses
[VMFest][vmfest] to turn your local VirtualBox into a local cloud
provider. This option is generally faster and definitely cheaper, but
needs some configuration, and some extra RAM on your laptop.

(We develop 99% of the time on VirtualBox, and only test every now
and then on public cloud infrastructure).

## Preparing for Amazon AWS

In order to use Amazon AWS as your target infrastructure provider, you
will need:

1. An active account with Amazon AWS
2. Generate the Amazon AWS API credentials (will be used by Pallet)
 
### Create an Amazon AWS Account

If you already have an Amazon AWS account, you can skip this step.
Otherwise:

1. Go to http://aws.amazon.com, and select `Sign-up Now`. Sign in to
your existing Amazon account or create a new one.
2. Go to http://aws.amazon.com/ec2, and select `Sign Up for Amazon
EC2`.
3. Enter your credit card information.
4. Complete your signup for the Amazon EC2 service.

After signing up, you should end up at the EC2 console.

### Obtain Your Amazon API Credentials

1. Log into your [Amazon AWS Console](https://console.aws.amazon.com/) if you are not already there

2. At the top of the page to the right, you'll find your name.
Clicking on it will present a menu. Click on the `Security
Credentials` option to go to the page that contains your credentials.

3. Scroll down to your Access Keys, and get the Access Key ID. This is
your `identity`.

4. Click on `Show` link to the right of your Access Key ID to show the
corresponding Secret Access Key. This is your `credential`.

Keep the `identity` and `credential` around for the bootstrapping of
your `learn-pallet` session.

## Preparing for VirtualBox

To use Pallet on VirtualBox you will need to have
[VirtualBox 4.12 or newer][vbox] on your computer. Remember that if
you use Windows, you will need to use Amazon EC2 instead of
VirtualBox.

If your computer is running on OSX or Linux (except Debian Weezy and
Ubuntu 12 or later) then you want to configure `learn-pallet` to
connect to VirtualBox via XPCOM. In this case there is no further
configuration to be done.

For Debian Weezy and Ubuntu 12+ or later, you will want `learn-pallet`
to use Web Services to connect to VirtualBox. In this case you will
need to perform the following configuration steps:

1. run the following command at the shell ( __only this once__):

    ```
    bash$ VBoxManage setproperty websrvauthlibrary null
    ````

1. Start the VirtualBox server by running this at the shell and leave
   it running (you'll need to do this every time you want to use
   Pallet with VirtualBox:

    ```bash  
    bash$ vboxwebsrv -t0
    ```  

[gen-ssh-keys]: https://help.github.com/articles/generating-ssh-keys
[java]: http://www.oracle.com/technetwork/java/javase/downloads/index.html
[jclouds]: http://www.jclouds.org/documentation/reference/supported-providers/
[lein]: http://leiningen.org/#install
[lein-win]: http://leiningen-win-installer.djpowell.net
[vbox]: https://virtualbox.org
[vbox-dl]: https://www.virtualbox.org/wiki/Downloads
[vmfest]: https://github.com/tbatchelli/vmfest

[pallet-ml]: https://groups.google.com/forum/?fromgroups#!forum/pallet-clj
[freenode]: http://freenode.net/irc_servers.shtml
[learn-pallet-issues]: https://github.com/pallet/learn-pallet/issues
[palletops-tweet]: https://twitter.com/palletops
