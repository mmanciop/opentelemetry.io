---
title: Packaging SIG first repository
linkTitle: Packaging SIG first repository
date: 2026-07-20
author: >-
  [Antoine Toulme](https://github.com/atoulme)(Splunk)
  [Michele Mancioppi](https://github.com/mmanciop)(Dash0)
# prettier-ignore
cSpell:ignore: Agrawal Alff Anuraag anuraaga Ashpole Bachert Baeyens brettmc carlosalberto codeboten Danielson dashpole jaydeluca Kielek Kiełkowicz Liudmila lmolkova Lüchinger maryliag Molkova Nevay ocelotl Pellard pellared Shkuro Sloughter Solomchenko trask tsloughter Yahn Yevhenii ysolomchenko yurishkuro zeitlinger Mancioppi
---

## What happened?

The Packaging SIG has been established earlier this year and is setting up a repository to try its first packages. We want to hear from the community on how this is going. Read on for more!

## Packaging SIG

The Packaging SIG is officially [established](https://github.com/open-telemetry/community/blob/main/projects/packaging.md) as of May 2026.
> The goal of the Packaging SIG is to provide a product-like, idiomatic experience to provide a seamless experience of monitoring applications running on (virtual) hosts through a combination of the [OpenTelemetry Injector](https://github.com/open-telemetry/opentelemetry-injector) injecting SDKs and auto-instrumentation packages, [OpenTelemetry eBPF Instrumentation (OBI)](https://github.com/open-telemetry/opentelemetry-ebpf-instrumentation), and the OpenTelemetry Collector.

The Packaging SIG works towards the [Stable By Default vision](https://opentelemetry.io/blog/2025/stability-proposal-announcement/) of the project.

The Packaging SIG works in https://github.com/open-telemetry/opentelemetry-packaging, discusses on the CNCF slack under the [#otel-packaging channel](https://cloud-native.slack.com/archives/C0AD17NMBLZ) and meets [weekly Thursdays at 8:30am PT](https://github.com/open-telemetry/community#sig-packaging). Please feel free to come by and say hi!

## The first OpenTelemetry Repositories

The work took place in two separate PRs:
* [#10](https://github.com/open-telemetry/opentelemetry-packaging/pull/10) on a specification for the way the packages should be organized
* [#18](https://github.com/open-telemetry/opentelemetry-packaging/pull/18) on the implementation of the specification, extensive testing, and publication to GitHub Pages.

Both were lead by Michele Mancioppi, with reviews of other maintainers across the project.

This delivery allows you to set up the injector and OpenTelemetry SDKs on a Linux box with deb or rpm support.

## Now, you try

The project has [defined steps to try this out now](https://github.com/open-telemetry/opentelemetry-packaging#installing) - for the impatient:

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

Read the [whole instructions](https://github.com/open-telemetry/opentelemetry-packaging#installing) to learn more about the options and where to send data.

## The Future

### Towards production
The packaging effort is new! There are scalability and security enhancements in our immediate roadmap:

The repository is hosted on GitHub under GitHub Pages. This is not meant for production workloads, and we will look for [production-grade hosting solutions](https://github.com/open-telemetry/opentelemetry-packaging/issues/4).

[We don't sign packages yet](https://github.com/open-telemetry/opentelemetry-packaging/issues/23). We will find a secure solution that still allows us to quickly release without creating manual, error-prone steps.

### Collector packaging

We will now work to add the OpenTelemetry packages. They are right now published under opentelemetry-collector-releases. Track this [issue](https://github.com/open-telemetry/opentelemetry-collector-releases/issues/1561) for more information.

## Thank you!

A big thank you to the contributors who have participated in this effort, starting with the main instigator, Michele Mancioppi.

Thank you as well to the many reviewers of the packaging SIG proposal and initial implementation!

