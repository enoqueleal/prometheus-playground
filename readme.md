# Setup Prometheus Playground

## Step 1: Create a new black project in [spring initializr](https://start.spring.io/)

## Step 2: Insert micrometer dependency in your project, [download here](https://micrometer.io/docs/installing)

## Step 3: Insert prometheus properties em application.properties or yml
``` properties
application.name=prometheus-playground
management.metrics.enable.jvm=true
management.endpoints.web.exposure.include=health,info,prometheus,metrics
```

## Step 4: Download Prometheus

```bash
$ curl -O https://github.com/prometheus/prometheus/releases/download/v2.39.0-rc.0/prometheus-2.39.0-rc.0.darwin-amd64.tar.gz
$ tar -zxvf prometheus-2.39.0-rc.0.darwin-amd64.tar.gz
```

## Step 5: Configure a new target on prometheus.yml
``` yaml
- job_name: "prometheus-playground"
  metrics_path: /actuator/prometheus
  static_configs:
    - targets: ["localhost:8080"]
      labels:
        application: prometheus-playground
```

## Step 6: Start Prometheus in your workstation
```bash
$ ./prometheus --config.file=prometheus.yml
```

## Step 7: Download Grafana

```bash
$ curl -O https://dl.grafana.com/enterprise/release/grafana-enterprise-9.2.0-beta1.darwin-amd64.tar.gz
$ tar -zxvf grafana-enterprise-9.2.0-beta1.darwin-amd64.tar.gz
```


## Step 8: Start Grafana in your workstation

``` bash
$ ./bin/grafana-server web
```

## Step 9: Download or import a Spring Boot Statistics template in Grafana repository

Grafana [template](https://grafana.com/grafana/dashboards/12464-spring-boot-statistics/)

ID: 12464
