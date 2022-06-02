# Knative Release

How to release a `knative.dev` repository.

## Release Schedule

| Release | Release Date | Serving        | Eventing            | PKG cut    | Unpin repos
| ------- | ------------ | -------------- | --------------------| ---------- | -----------
| v1.5    | 2022-05-31   | dprotaso       | gab-satchi          | 2022-05-24 | 2022-06-01
| v1.6    | 2022-07-12   | psschwei       | evankanderson       | 2022-07-05 | 2022-07-13
| v1.7    | 2022-08-23   | dprotaso       | matzew              | 2022-08-16 | 2022-08-24
| v1.8    | 2022-10-04   | nak3           | lionelvillard       | 2022-09-27 | 2022-10-05
| v1.9    | 2022-11-15   | psschwei       | evankanderson       | 2022-11-08 | 2022-11-16

[Roster](./ROSTER.md) has the roster for each Knative release.

[Instructions](./INSTRUCTIONS.md) has the instructions for cutting a release.

## Repo Releasability

| Repo | Release | Releasability | Nightly |
| --- | --- | --- | --- |
| [knative.dev/pkg](https://github.com/knative/pkg) | N/A | [![Releasability](https://github.com/knative/pkg/workflows/Releasability/badge.svg)](https://github.com/knative/pkg/actions/workflows/knative-releasability.yaml)        | N/A |
| [knative.dev/networking](https://github.com/knative/networking)  | N/A                 | [![Releasability](https://github.com/knative/networking/workflows/Releasability/badge.svg)](https://github.com/knative/networking/actions/workflows/knative-releasability.yaml)              | N/A |
| [knative.dev/caching](https://github.com/knative/caching)      | N/A      | [![Releasability](https://github.com/knative/caching/workflows/Releasability/badge.svg)](https://github.com/knative/caching/actions/workflows/knative-releasability.yaml)                 | N/A |
| [knative.dev/reconciler-test](https://github.com/knative-sandbox/reconciler-test) | N/A | [![Releasability](https://github.com/knative-sandbox/reconciler-test/workflows/Releasability/badge.svg)](https://github.com/knative-sandbox/reconciler-test/actions/workflows/knative-releasability.yaml) | N/A |
| [knative.dev/control-protocol](https://github.com/knative-sandbox/control-protocol)| N/A | [![Releasability](https://github.com/knative-sandbox/control-protocol/workflows/Releasability/badge.svg)](https://github.com/knative-sandbox/control-protocol/actions/workflows/knative-releasability.yaml) | N/A |
| [knative.dev/serving](https://github.com/knative/serving)                             | [![Releases](https://img.shields.io/github/release-pre/knative/serving.svg?sort=semver)](https://github.com/knative/serving/releases)                                     | [![Releasability](https://github.com/knative/serving/workflows/Releasability/badge.svg)](https://github.com/knative/serving/actions/workflows/knative-releasability.yaml)                   | [![Nightly](https://prow.knative.dev/badge.svg?jobs=nightly_serving_main_periodic)](https://prow.knative.dev?job=nightly_serving_main_periodic)                   |
| [knative.dev/net-certmanager](https://github.com/knative-sandbox/net-certmanager)     | [![Releases](https://img.shields.io/github/release-pre/knative-sandbox/net-certmanager.svg?sort=semver)](https://github.com/knative-sandbox/net-certmanager/releases)     | [![Releasability](https://github.com/knative-sandbox/net-certmanager/workflows/Releasability/badge.svg)](https://github.com/knative-sandbox/net-certmanager/actions/workflows/knative-releasability.yaml)   | [![Nightly](https://prow.knative.dev/badge.svg?jobs=nightly_net-certmanager_main_periodic)](https://prow.knative.dev?job=nightly_net-certmanager_main_periodic)   |
| [knative.dev/net-contour](https://github.com/knative-sandbox/net-contour)             | [![Releases](https://img.shields.io/github/release-pre/knative-sandbox/net-contour.svg?sort=semver)](https://github.com/knative-sandbox/net-contour/releases)             | [![Releasability](https://github.com/knative-sandbox/net-contour/workflows/Releasability/badge.svg)](https://github.com/knative-sandbox/net-contour/actions/workflows/knative-releasability.yaml)       | [![Nightly](https://prow.knative.dev/badge.svg?jobs=nightly_net-contour_main_periodic)](https://prow.knative.dev?job=nightly_net-contour_main_periodic)       |
| [knative.dev/net-http01](https://github.com/knative-sandbox/net-http01)               | [![Releases](https://img.shields.io/github/release-pre/knative-sandbox/net-http01.svg?sort=semver)](https://github.com/knative-sandbox/net-http01/releases)               | [![Releasability](https://github.com/knative-sandbox/net-http01/workflows/Releasability/badge.svg)](https://github.com/knative-sandbox/net-http01/actions/workflows/knative-releasability.yaml)        | [![Nightly](https://prow.knative.dev/badge.svg?jobs=nightly_net-http01_main_periodic)](https://prow.knative.dev?job=nightly_net-http01_main_periodic)        |
| [knative.dev/net-istio](https://github.com/knative-sandbox/net-istio)                 | [![Releases](https://img.shields.io/github/release-pre/knative-sandbox/net-istio.svg?sort=semver)](https://github.com/knative-sandbox/net-istio/releases)                 | [![Releasability](https://github.com/knative-sandbox/net-istio/workflows/Releasability/badge.svg)](https://github.com/knative-sandbox/net-istio/actions/workflows/knative-releasability.yaml)         | [![Nightly](https://prow.knative.dev/badge.svg?jobs=nightly_net-istio_main_periodic)](https://prow.knative.dev?job=nightly_net-istio_main_periodic)         |
| [knative.dev/net-kourier](https://github.com/knative-sandbox/net-kourier)             | [![Releases](https://img.shields.io/github/release-pre/knative-sandbox/net-kourier.svg?sort=semver)](https://github.com/knative-sandbox/net-kourier/releases)             | [![Releasability](https://github.com/knative-sandbox/net-kourier/workflows/Releasability/badge.svg)](https://github.com/knative-sandbox/net-kourier/actions/workflows/knative-releasability.yaml)       | [![Nightly](https://prow.knative.dev/badge.svg?jobs=nightly_net-kourier_main_periodic)](https://prow.knative.dev?job=nightly_net-kourier_main_periodic)       |
| [knative.dev/net-gateway-api](https://github.com/knative-sandbox/net-gateway-api)             | [![Releases](https://img.shields.io/github/release-pre/knative-sandbox/net-gateway-api.svg?sort=semver)](https://github.com/knative-sandbox/net-gateway-api/releases)             | [![Releasability](https://github.com/knative-sandbox/net-gateway-api/workflows/Releasability/badge.svg)](https://github.com/knative-sandbox/net-gateway-api/actions/workflows/knative-releasability.yaml)       | [![Nightly](https://prow.knative.dev/badge.svg?jobs=nightly_net-gateway-api_main_periodic)](https://prow.knative.dev?job=nightly_net-gateway-api_main_periodic)       |
| [knative.dev/eventing](https://github.com/knative/eventing)                           | [![Releases](https://img.shields.io/github/release-pre/knative/eventing.svg?sort=semver)](https://github.com/knative/eventing/releases)                                   | [![Releasability](https://github.com/knative/eventing/workflows/Releasability/badge.svg)](https://github.com/knative/eventing/actions/workflows/knative-releasability.yaml)                  | [![Nightly](https://prow.knative.dev/badge.svg?jobs=nightly_eventing_main_periodic)](https://prow.knative.dev?job=nightly_eventing_main_periodic)                  |
| [knative.dev/sample-controller](https://github.com/knative-sandbox/sample-controller) | [![Releases](https://img.shields.io/github/release-pre/knative-sandbox/sample-controller.svg?sort=semver)](https://github.com/knative-sandbox/sample-controller/releases) | [![Releasability](https://github.com/knative-sandbox/sample-controller/workflows/Releasability/badge.svg)](https://github.com/knative-sandbox/sample-controller/actions/workflows/knative-releasability.yaml) | [![Nightly](https://prow.knative.dev/badge.svg?jobs=nightly_sample-controller_main_periodic)](https://prow.knative.dev?job=nightly_sample-controller_main_periodic) |
| [knative.dev/eventing-ceph](https://github.com/knative-sandbox/eventing-ceph)                 | [![Releases](https://img.shields.io/github/release-pre/knative-sandbox/eventing-ceph.svg?sort=semver)](https://github.com/knative-sandbox/eventing-ceph/releases)                 | [![Releasability](https://github.com/knative-sandbox/eventing-ceph/workflows/Releasability/badge.svg)](https://github.com/knative-sandbox/eventing-ceph/actions/workflows/knative-releasability.yaml)         | [![Nightly](https://prow.knative.dev/badge.svg?jobs=nightly_eventing-ceph_main_periodic)](https://prow.knative.dev?job=nightly_eventing-ceph_main_periodic)         |
| [knative.dev/eventing-kogito](https://github.com/knative-sandbox/eventing-kogito) | [![Releases](https://img.shields.io/github/release-pre/knative-sandbox/eventing-kogito.svg?sort=semver)](https://github.com/knative-sandbox/eventing-kogito/releases) | [![Releasability](https://github.com/knative-sandbox/eventing-kogito/workflows/Releasability/badge.svg)](https://github.com/knative-sandbox/eventing-kogito/actions/workflows/knative-releasability.yaml) | [![Nightly](https://prow.knative.dev/badge.svg?jobs=nightly_eventing-kogito_main_periodic)](https://prow.knative.dev?job=nightly_eventing-kogito_main_periodic) |
| [knative.dev/eventing-rabbitmq](https://github.com/knative-sandbox/eventing-rabbitmq)         | [![Releases](https://img.shields.io/github/release-pre/knative-sandbox/eventing-rabbitmq.svg?sort=semver)](https://github.com/knative-sandbox/eventing-rabbitmq/releases)         | [![Releasability](https://github.com/knative-sandbox/eventing-rabbitmq/workflows/Releasability/badge.svg)](https://github.com/knative-sandbox/eventing-rabbitmq/actions/workflows/knative-releasability.yaml)     | [![Nightly](https://prow.knative.dev/badge.svg?jobs=nightly_eventing-rabbitmq_main_periodic)](https://prow.knative.dev?job=nightly_eventing-rabbitmq_main_periodic)     |
| [knative.dev/sample-source](https://github.com/knative-sandbox/sample-source)                 | [![Releases](https://img.shields.io/github/release-pre/knative-sandbox/sample-source.svg?sort=semver)](https://github.com/knative-sandbox/sample-source/releases)                 | [![Releasability](https://github.com/knative-sandbox/sample-source/workflows/Releasability/badge.svg)](https://github.com/knative-sandbox/sample-source/actions/workflows/knative-releasability.yaml)         | [![Nightly](https://prow.knative.dev/badge.svg?jobs=nightly_sample-source_main_periodic)](https://prow.knative.dev?job=nightly_sample-source_main_periodic)         |
| [knative.dev/client](https://github.com/knative/client)     | [![Releases](https://img.shields.io/github/release-pre/knative/client.svg?sort=semver)](https://github.com/knative/client/releases)     | [![Releasability](https://github.com/knative/client/workflows/Releasability/badge.svg)](https://github.com/knative/client/actions/workflows/knative-releasability.yaml)   | [![Nightly](https://prow.knative.dev/badge.svg?jobs=nightly_client_main_periodic)](https://prow.knative.dev?job=nightly_client_main_periodic) |
| [knative.dev/eventing-kafka](https://github.com/knative-sandbox/eventing-kafka)               | [![Releases](https://img.shields.io/github/release-pre/knative-sandbox/eventing-kafka.svg?sort=semver)](https://github.com/knative-sandbox/eventing-kafka/releases)               | [![Releasability](https://github.com/knative-sandbox/eventing-kafka/workflows/Releasability/badge.svg)](https://github.com/knative-sandbox/eventing-kafka/actions/workflows/knative-releasability.yaml)        | [![Nightly](https://prow.knative.dev/badge.svg?jobs=nightly_eventing-kafka_main_periodic)](https://prow.knative.dev?job=nightly_eventing-kafka_main_periodic)        |
| [knative.dev/eventing-redis](https://github.com/knative-sandbox/eventing-redis)   | [![Releases](https://img.shields.io/github/release-pre/knative-sandbox/eventing-redis.svg?sort=semver)](https://github.com/knative-sandbox/eventing-redis/releases)   | [![Releasability](https://github.com/knative-sandbox/eventing-redis/workflows/Releasability/badge.svg)](https://github.com/knative-sandbox/eventing-redis/actions/workflows/knative-releasability.yaml)  | [![Nightly](https://prow.knative.dev/badge.svg?jobs=nightly_eventing-redis_main_periodic)](https://prow.knative.dev?job=nightly_eventing-redis_main_periodic)  |
| [knative.dev/eventing-github](https://github.com/knative-sandbox/eventing-github) | [![Releases](https://img.shields.io/github/release-pre/knative-sandbox/eventing-github.svg?sort=semver)](https://github.com/knative-sandbox/eventing-github/releases) | [![Releasability](https://github.com/knative-sandbox/eventing-github/workflows/Releasability/badge.svg)](https://github.com/knative-sandbox/eventing-github/actions/workflows/knative-releasability.yaml) | [![Nightly](https://prow.knative.dev/badge.svg?jobs=nightly_eventing-github_main_periodic)](https://prow.knative.dev?job=nightly_eventing-github_main_periodic) |
| [knative.dev/eventing-gitlab](https://github.com/knative-sandbox/eventing-gitlab) | [![Releases](https://img.shields.io/github/release-pre/knative-sandbox/eventing-gitlab.svg?sort=semver)](https://github.com/knative-sandbox/eventing-gitlab/releases) | [![Releasability](https://github.com/knative-sandbox/eventing-gitlab/workflows/Releasability/badge.svg)](https://github.com/knative-sandbox/eventing-gitlab/actions/workflows/knative-releasability.yaml) | [![Nightly](https://prow.knative.dev/badge.svg?jobs=nightly_eventing-gitlab_main_periodic)](https://prow.knative.dev?job=nightly_eventing-gitlab_main_periodic) |
| [knative.dev/eventing-kafka-broker](https://github.com/knative-sandbox/eventing-kafka-broker) | [![Releases](https://img.shields.io/github/release-pre/knative-sandbox/eventing-kafka-broker.svg?sort=semver)](https://github.com/knative-sandbox/eventing-kafka-broker/releases) | [![Releasability](https://github.com/knative-sandbox/eventing-kafka-broker/workflows/Releasability/badge.svg)](https://github.com/knative-sandbox/eventing-kafka-broker/actions/workflows/knative-releasability.yaml) | [![Nightly](https://prow.knative.dev/badge.svg?jobs=nightly_eventing-kafka-broker_main_periodic)](https://prow.knative.dev?job=nightly_eventing-kafka-broker_main_periodic) |
| [knative.dev/eventing-autoscaler-keda](https://github.com/knative-sandbox/eventing-autoscaler-keda) | [![Releases](https://img.shields.io/github/release-pre/knative-sandbox/eventing-autoscaler-keda.svg?sort=semver)](https://github.com/knative-sandbox/eventing-autoscaler-keda/releases) | [![Releasability](https://github.com/knative-sandbox/eventing-autoscaler-keda/workflows/Releasability/badge.svg)](https://github.com/knative-sandbox/eventing-autoscaler-keda/actions/workflows/knative-releasability.yaml) | [![Nightly](https://prow.knative.dev/badge.svg?jobs=nightly_eventing-autoscaler-keda_main_periodic)](https://prow.knative.dev?job=nightly_eventing-autoscaler-keda_main_periodic) |
| [knative.dev/kn-plugin-admin](https://github.com/knative-sandbox/kn-plugin-admin) | [![Releases](https://img.shields.io/github/release-pre/knative-sandbox/kn-plugin-admin.svg?sort=semver)](https://github.com/knative-sandbox/kn-plugin-admin/releases) | [![Releasability](https://github.com/knative-sandbox/kn-plugin-admin/workflows/Releasability/badge.svg)](https://github.com/knative-sandbox/kn-plugin-admin/actions/workflows/knative-releasability.yaml) | [![Nightly](https://prow.knative.dev/badge.svg?jobs=nightly_kn-plugin-admin_main_periodic)](https://prow.knative.dev?job=nightly_kn-plugin-admin_main_periodic) |
| [knative.dev/kn-plugin-event](https://github.com/knative-sandbox/kn-plugin-event) | [![Releases](https://img.shields.io/github/release-pre/knative-sandbox/kn-plugin-event.svg?sort=semver)](https://github.com/knative-sandbox/kn-plugin-event/releases) | [![Releasability](https://github.com/knative-sandbox/kn-plugin-event/workflows/Releasability/badge.svg)](https://github.com/knative-sandbox/kn-plugin-event/actions/workflows/knative-releasability.yaml) | [![Nightly](https://prow.knative.dev/badge.svg?jobs=nightly_kn-plugin-event_main_periodic)](https://prow.knative.dev?job=nightly_kn-plugin-event_main_periodic) |
| [knative.dev/kn-plugin-source-kafka](https://github.com/knative-sandbox/kn-plugin-source-kafka) | [![Releases](https://img.shields.io/github/release-pre/knative-sandbox/kn-plugin-source-kafka.svg?sort=semver)](https://github.com/knative-sandbox/kn-plugin-source-kafka/releases) | [![Releasability](https://github.com/knative-sandbox/kn-plugin-source-kafka/workflows/Releasability/badge.svg)](https://github.com/knative-sandbox/kn-plugin-source-kafka/actions/workflows/knative-releasability.yaml) | [![Nightly](https://prow.knative.dev/badge.svg?jobs=nightly_kn-plugin-source-kafka_main_periodic)](https://prow.knative.dev?job=nightly_kn-plugin-source-kafka_main_periodic) |
| [knative.dev/kn-plugin-source-kamelet](https://github.com/knative-sandbox/kn-plugin-source-kamelet) | [![Releases](https://img.shields.io/github/release-pre/knative-sandbox/kn-plugin-source-kamelet.svg?sort=semver)](https://github.com/knative-sandbox/kn-plugin-source-kamelet/releases) | [![Releasability](https://github.com/knative-sandbox/kn-plugin-source-kamelet/workflows/Releasability/badge.svg)](https://github.com/knative-sandbox/kn-plugin-source-kamelet/actions/workflows/knative-releasability.yaml) | [![Nightly](https://prow.knative.dev/badge.svg?jobs=nightly_kn-plugin-source-kamelet_main_periodic)](https://prow.knative.dev?job=nightly_kn-plugin-source-kamelet_main_periodic) |
| [knative.dev/kn-plugin-quickstart](https://github.com/knative-sandbox/kn-plugin-quickstart) | [![Releases](https://img.shields.io/github/release-pre/knative-sandbox/kn-plugin-quickstart.svg?sort=semver)](https://github.com/knative-sandbox/kn-plugin-quickstart/releases) | [![Releasability](https://github.com/knative-sandbox/kn-plugin-quickstart/workflows/Releasability/badge.svg)](https://github.com/knative-sandbox/kn-plugin-quickstart/actions/workflows/knative-releasability.yaml) | [![Nightly](https://prow.knative.dev/badge.svg?jobs=nightly_kn-plugin-quickstart_main_periodic)](https://prow.knative.dev?job=nightly_kn-plugin-quickstart_main_periodic) |
| [knative.dev/operator](https://github.com/knative/operator) | [![Releases](https://img.shields.io/github/release-pre/knative/operator.svg?sort=semver)](https://github.com/knative/operator/releases) | [![Releasability](https://github.com/knative/operator/workflows/Releasability/badge.svg)](https://github.com/knative/operator/actions/workflows/knative-releasability.yaml) | [![Nightly](https://prow.knative.dev/badge.svg?jobs=nightly_operator_main_periodic)](https://prow.knative.dev?job=nightly_operator_main_periodic) |
| [knative.dev/docs](https://github.com/knative/docs)       | N/A      | N/A    | N/A                                                                                   |
