---
title: One-command monitoring for yiur Linux hosts
linkTitle: One-command monitoring for yiur Linux hosts
date: 2026-07-20
author: >-
  [Antoine Toulme](https://github.com/atoulme)(Splunk)
  [Michele Mancioppi](https://github.com/mmanciop)(Dash0)
# prettier-ignore
cSpell:ignore: Agrawal Alff Anuraag anuraaga Ashpole Bachert Baeyens brettmc carlosalberto codeboten Danielson dashpole jaydeluca Kielek Kiełkowicz Liudmila lmolkova Lüchinger maryliag Molkova Nevay ocelotl Pellard pellared Shkuro Sloughter Solomchenko trask tsloughter Yahn Yevhenii ysolomchenko yurishkuro zeitlinger Mancioppi
---

## The dream

Wouldn't it be nice to be able to set up your Linux hosts with one command so that all the apps running on top of it would be automatically monitored with OpenTelemetry?

You know, something like:

```
{apt|yum} install opentelemetry
```

Well, guess what!

## What happened?

The Packaging SIG has been established earlier this year and is setting up a repository to try its first packages, which enable you to install with one command the [OpenTelemetry Injector](https://github.com/open-telemetry/opentelemetry-injector) and auto-instrumentation packages based on the [OpenTelemetry Java Agent](https://github.com/open-telemetry/opentelemetry-java-instrumentation), the [OpenTelemetry .NET Automatic Instrumentation](https://github.com/open-telemetry/opentelemetry-dotnet-instrumentation), the [OpenTelemetry Node.ja Automatic Instrumentation](https://github.com/open-telemetry/opentelemetry-js-contrib/blob/main/packages/auto-instrumentations-node/README.md) and the OpenTelemetry Oython SDK and instrumentations.

The packages are available for the DEB and RPM package management.

## OpenTelemetry as a system dependency

Trying out the new packages is as easy as:
1. Installing the packages
2. Configuring where to send the data
3. Restart your Java, .NET, Node.js and Python processes 

### Installing the packages

We created a started repo on GitHub Pages.
(It is not the final location, so expect that to change in the future.)

On Debian, Ubuntu and derivatives, add the APT repository with:

```sh
echo "deb [trusted=yes] https://open-telemetry.github.io/opentelemetry-packaging/debian stable main" | sudo tee /etc/apt/sources.list.d/opentelemetry.list
sudo apt update
sudo apt install opentelemetry
```

On Fedora, RHEL, and derivatives, add the YUM repository:

```sh
cat <<EOF | sudo tee /etc/yum.repos.d/opentelemetry.repo
[opentelemetry]
name=OpenTelemetry Auto-Instrumentation System Packages
baseurl=https://open-telemetry.github.io/opentelemetry-packaging/rpm/packages
enabled=1
gpgcheck=0
EOF
sudo dnf install opentelemetry
```

### Configuring where to send the data

TODO

Read the [whole instructions](https://github.com/open-telemetry/opentelemetry-packaging#installing) to learn more about the options and where to send data.

### Installing the Collector

TODO

## Brought to you by the Packaging SIG

The Packaging SIG is officially [established](https://github.com/open-telemetry/community/blob/main/projects/packaging.md) as of May 2026.
> The goal of the Packaging SIG is to provide a product-like, idiomatic experience to provide a seamless experience of monitoring applications running on (virtual) hosts through a combination of the [OpenTelemetry Injector](https://github.com/open-telemetry/opentelemetry-injector) injecting SDKs and auto-instrumentation packages, [OpenTelemetry eBPF Instrumentation (OBI)](https://github.com/open-telemetry/opentelemetry-ebpf-instrumentation), and the OpenTelemetry Collector.

The Packaging SIG works towards the [Stable By Default vision](https://opentelemetry.io/blog/2025/stability-proposal-announcement/) of the project.

If you want to reach the Packaging SIG, we work in the https://github.com/open-telemetry/opentelemetry-packaging repository, discuss in the [#otel-packaging channel](https://cloud-native.slack.com/archives/C0AD17NMBLZ)  of the CNCF slack, and meet [weekly Thursdays at 8:30am PT](https://github.com/open-telemetry/community#sig-packaging).

Come by and say hi!

## The Future(TM)

### Towards production
The packaging effort is new!
There are scalability and security enhancements in our immediate roadmap.

The repository is hosted on GitHub under GitHub Pages.
This is not meant for production workloads, and we will look for [production-grade hosting solutions](https://github.com/open-telemetry/opentelemetry-packaging/issues/4).

[We don't sign packages yet](https://github.com/open-telemetry/opentelemetry-packaging/issues/23).
We will find a secure solution that still allows us to quickly release without creating manual, error-prone steps.

### Collector packaging

We want to incorporate the OpenTelemetry Collector packages to live alongside the others.
Currently, .deb and .rpm Collector packages are published as release artifacts in the [Opentelemetry Collector Releases](https://github.com/open-telemetry/opentelemetry-collector-releases) repository.
Track this [issue](https://github.com/open-telemetry/opentelemetry-collector-releases/issues/1561) for more information.

## Thank you!

A big thank you to the contributors who have participated in this effort.

Thank you as well to the many reviewers of the packaging SIG proposal and initial implementation!

