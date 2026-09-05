# cf_kind_local_2026

[![](https://img.shields.io/badge/cf-kind-purple.svg)](https://github.com/cloudfoundry/kind-deployment)
[![](https://img.shields.io/badge/nodejs-buildpack-blue.svg)](https://github.com/cloudfoundry/nodejs-buildpack)

*Some major changes.*

> Still considered a technical improvement over plain **Kubernetes** (simplication of **Kubernetes Deployments** which is the main way I've encountered it in past work - usually with Pivotal products). 

> `cf push -f manifest.yaml` simplifies the sequences and explicit configuration required when using `kubectl apply -f manifest.yaml`.

> https://www.systemdesignhandbook.com/guides/cloud-foundry-vs-kubernetes/

> https://softwarehut.com/blog/tech/cloud-foundry-vs-kubernetes

## Changes for 2026

1. **PCF Dev** is deprecated and [kind-deployment](https://github.com/cloudfoundry/kind-deployment) is now the officially supported way to test **Cloud Foundry** locally.
1. **Cloud Foundry** is now usually used with `kub`.
1. [`Spring Cloud CLI`](https://github.com/Thoughtscript/java_stuff/tree/master/spring-cloud-cli) has largely been decoupled from **Cloud Foundry** (cloud or otherwise). The **Cloud Foundry CLI** remains the primary way to interact with **Cloud Foundry** (though often still with Spring integration/extensions).
1. **Spring Cloud Netflix Eureka** is commonly used still in **Cloud Foundry**.
1. Pivotal divested itself a long time ago from **Cloud Foundry**.
1. **Spring Boot Actuator** - [Common Application Properties](https://docs.spring.io/spring-boot/appendix/application-properties/index.html#application-properties.actuator.management.cloudfoundry.enabled) stills provides integration with **Cloud Foundry**.

## Setup and Use

```bash
make up
brew install cloudfoundry/tap/cf-cli@8
brew trust cloudfoundry/tap
brew link cloudfoundry/tap/cf-cli@8 
make login
make bootstrap
cf push -f examples/hello-js/manifest.yaml
```

[buildpacks](https://docs.cloudfoundry.org/adminguide/buildpacks.html) will need to be supplied AND in URL format (at least through the method above):

```yaml
  ...
  buildpacks:
    - https://github.com/cloudfoundry/nodejs-buildpack
```

> Official buildpacks: https://github.com/cloudfoundry?q=buildpack

Useful commands:
```bash
cf restage hello-js  
cf logs hello-js --recent 

cf apps
cf tasks hello-js
cf events hello-js
```

## Resources and Links

1. https://github.com/cloudfoundry/kind-deployment
1. https://docs.cloudfoundry.org/adminguide/buildpacks.html
1. https://github.com/cloudfoundry?q=buildpack
1. https://cli.cloudfoundry.org/en-US/v6/
1. https://www.systemdesignhandbook.com/guides/cloud-foundry-vs-kubernetes/
1. https://softwarehut.com/blog/tech/cloud-foundry-vs-kubernetes
1. https://docs.spring.io/spring-boot/reference/actuator/cloud-foundry.html
1. https://docs.spring.io/spring-cloud-cloudfoundry/docs/current/reference/html/
1. https://docs.cloudfoundry.org/buildpacks/java/getting-started-deploying-apps/gsg-spring.html