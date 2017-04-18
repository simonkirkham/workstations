# Workstations

<!--
TODO: getting started - home var
TODO: customization - reprovision note
TODO: contributing - extending: new workstations, custom provisioning
-->

**Contents** [Overview] | [Getting started] | [Usage] | [Next steps] | [Contributing] | [Resources]  

This repository contains Windows workstations for .NET, SQL Server, infrastructure and Java development using Vagrant and VirtualBox.

## Overview

This repository contains Windows-based workstations for the following purposes:

* [.NET development] with Visual Studio.
* [SQL Server development] with SQL Server Management Studio.
* [Infrastructure development] with Chef, Packer, Terraform and AWS.
* [Java development] with IntelliJ IDEA.

All of them support an easy, source-controlled way of installing and configuring the most common development tools for the related stacks and the management of the sources of your projects, based on [Vagrant][VagrantHome] and [VirtualBox][VirtualBoxHome]. This way you can easily recreate the same workstations anytime, anywhere, and instead of writing extensive documentation, you can simply share ready to use environments with your teammates and contributors.

The most common configuration options are also supported out of the box:

* Managing the core [OS] settings, installing features and additional packages.
* Working with [Git] and [SVN] repositories.
* Managing [NuGet] sources.
* Downloading [Vagrant] base boxes and pulling [Docker] images.
* Setting up [AWS] profiles.

Of course, you can extend these freely with your own configuration options and provisioning steps.

[Overview]: #overview

## Getting started

**Note** This section assumes you are familiar with the basics of [Vagrant][VagrantHome]. If that's not the case, it's recommended that you take a quick look at its [getting started guide][VagrantGettingStarted].  

**Note** The virtual environments have been tested on Windows hosts only, but they are supposed to run on any other platform as well. [Let me know][Contributing] if you encounter any issues and I'm glad to help.  

**Note** Booting a workstation for the first time can take a significant amount of time. If you have a slow connection, downloading the [base boxes][AtlasBoxes] (usually several GBs) might require some patience and retries. Also, provisioning (e.g. installing the custom tools not included in the base box) by default happens during the initial boot as well. However, starting the workstations again later, or creating another one from the already downloaded base box will be significantly faster.  

**Note** All the components of the workstations (including the core operating system) are installed from their publicly available [free or evaluation versions][PackerNotes].  

[Getting started]: #getting-started
[VagrantGettingStarted]: https://www.vagrantup.com/intro/getting-started/index.html
[AtlasBoxes]: https://atlas.hashicorp.com/gusztavvargadr
[PackerNotes]: https://github.com/gusztavvargadr/packer#notes

### Prerequisites

Follow the steps below to install the required tools:

1. Install the [Chef Development Kit][ChefDKInstallation].
1. Install [Vagrant][VagrantInstallation] and the following plugins:
    1. [vagrant-berkshelf][VagrantBerkshelfInstallation].
    1. [vagrant-reload][VagrantReloadInstallation].
1. Install [VirtualBox][VirtualBoxInstallation].
1. Disable virtualization platforms other than VirtualBox. On Windows, [disable Hyper-V][HyperVDisable], in case it is running.
1. Take a moment to realize that this might have been the last time you installed something for your workstations manually.

[VagrantInstallation]: https://www.vagrantup.com/docs/installation/
[VagrantBerkshelfInstallation]: https://github.com/berkshelf/vagrant-berkshelf#installation
[VagrantReloadInstallation]: https://github.com/aidanns/vagrant-reload#installation
[VirtualBoxInstallation]: https://www.virtualbox.org/wiki/Downloads
[ChefDKInstallation]: https://downloads.chef.io/chef-dk/
[HyperVDisable]: https://blogs.technet.microsoft.com/gmarchetti/2008/12/07/turning-hyper-v-on-and-off/

### Creating the workstations

Clone this repo and navigate to the root directory of the clone from your shell. Then follow the steps below to create any of the specific workstations.

#### .NET development

Boot the workstation:

```
$ cd src/dotnet
$ vagrant up
```

Connect to it via RDP or use the shell:

```
$ vagrant rdp
$ vagrant powershell
```

The workstation is created by default with the following tools installed and configured:

* [Windows Server 2016 Standard, Visual Studio 2015 Community, SQL Server 2014 Developer][.NETDevelopmentBox]
* [Docker]
* [Git]
* [NuGet]

[.NET development]: #net-development
[.NETDevelopmentBox]: https://atlas.hashicorp.com/gusztavvargadr/boxes/w16s-sql14d-vs15c

#### SQL Server development

Boot the workstation:

```
$ cd src/sql
$ vagrant up
```

Connect to it via RDP or use the shell:

```
$ vagrant rdp
$ vagrant powershell
```

The workstation is created by default with the following tools installed and configured:

* [Windows Server 2016 Standard, SQL Server 2014 Developer][SQLServerDevelopmentBox]
* [Docker]
* [Git]

[SQL Server development]: #sql-server-development
[SQLServerDevelopmentBox]: https://atlas.hashicorp.com/gusztavvargadr/boxes/w16s-sql14d

#### Infrastructure development

Boot the workstation:

```
$ cd src/infrastructure
$ vagrant up
```

Connect to it via RDP or use the shell:

```
$ vagrant rdp
$ vagrant powershell
```

The workstation is created by default with the following tools installed and configured:

* [Windows Server 2016 Standard][InfrastructureDevelopmentBox]
* [Docker]
* [Git]
* [ChefDK], [Packer], [Terraform]
* [Vagrant]
* [AWS]

[Infrastructure development]: #infrastructure-development
[InfrastructureDevelopmentBox]: https://atlas.hashicorp.com/gusztavvargadr/boxes/w16s
[ChefDK]: https://chocolatey.org/packages/chefdk
[Packer]: https://chocolatey.org/packages/packer
[Terraform]: https://chocolatey.org/packages/terraform

#### Java development

Boot the workstation:

```
$ cd src/java
$ vagrant up
```

Connect to it via RDP or use the shell:

```
$ vagrant rdp
$ vagrant powershell
```

The workstation is created by default with the following tools installed and configured:

* [Windows Server 2016 Standard][JavaDevelopmentBox]
* [Docker]
* [Git]
* [JDK], [Maven], [IntelliJ IDEA]

[Java development]: #java-development
[JavaDevelopmentBox]: https://atlas.hashicorp.com/gusztavvargadr/boxes/w16s
[JDK]: https://chocolatey.org/packages/jdk8
[Maven]: https://chocolatey.org/packages/maven
[IntelliJ IDEA]: https://chocolatey.org/packages/intellijidea-community

## Usage

**Note** This section assumes you are familiar with the basics of [Chef][ChefHome]. If that's not the case, it's recommended that you take a quick look at its [getting started guide][ChefGettingStarted].  

[ChefGettingStarted]: https://learn.chef.io/tutorials/

### Customizing provisioning

See below the complete list of provisioning customization options supported out of the box. 

#### OS

<!--
  * Configuring locales, time zone and environment variables.
  * Installing OS features.
  * Installing Chocolatey and native packages.
-->

[OS]: #os

#### Git

<!--
  * Installing the core Git tools.
  * Configuring Git settings.
  * Cloning public and private repositories.
-->

[Git]: #git

#### SVN

<!--
* SVN
  * Installing the core SVN tools.
  * Checking out public and private repositories.
-->

[SVN]: #svn

#### NuGet

<!--
* NuGet
  * Installing the core NuGet tools.
  * Adding public and private package sources.
-->

[NuGet]: #nuget

#### Vagrant

<!--
* Vagrant
  * Installing Vagrant itself and its plugins.
  * Adding base boxes.
-->

[Vagrant]: #vagrant

#### Docker

<!--
* Docker
  * Installing the core Docker tools.
  * Pulling images.
-->

[Docker]: #docker

#### AWS

<!--
* AWS
  * Installing the core AWS tools.
  * Setting up AWS CLI profiles.
-->

[AWS]: #aws

### Customizing Vagrant

<!--
multi machine
options

Besides the above, you can of course add any of your own customizations using the tools [Vagrant supports][VagrantProvisioning].

[VagrantProvisioning]: https://www.vagrantup.com/docs/provisioning/

-->

[Usage]: #usage

## Next steps

[Next steps]: #next-steps

## Contributing

Any feedback, [issues] and / or [pull requests] are welcome and greatly appreciated.

[Contributing]: #contributing
[Issues]: https://github.com/gusztavvargadr/workstations/issues
[Pull requests]: https://github.com/gusztavvargadr/workstations/pulls

## Resources

* [Vagrant][VagrantHome]
* [VirtualBox][VirtualBoxHome]
* [Chef][ChefHome]

[Resources]: #resources
[VagrantHome]: https://www.vagrantup.com/
[VirtualBoxHome]: https://www.virtualbox.org/
[ChefHome]: https://www.chef.io/chef/
