
# criar o projeto no initializer
$ https://start.spring.io/

# insert micrometer dependency
$ https://micrometer.io/docs/installing

# insert prometheus properties em application.properties or yml
``` properties
application.name=prometheus-playground
management.metrics.enable.jvm=true
management.endpoints.web.exposure.include=health,info,prometheus,metrics
```


# download prometheus
$ https://prometheus.io/download/

# config a new targe on prometheus.yml
``` yaml
- job_name: "prometheus-playground"
  metrics_path: /actuator/prometheus
  static_configs:
    - targets: ["localhost:8080"]
      labels:
        application: prometheus-playground
```

# start prometheus
```bash
$ ./prometheus --config.file=prometheus.yml
```

# download grafana
$ https://grafana.com/grafana/download?platform=mac

# start grafana
``` bash
$ ./bin/grafana-server web
```

# download grafana
$ https://grafana.com/grafana/dashboards/12464-spring-boot-statistics/

# download grafana template
$ https://grafana.com/grafana/dashboards/12464-spring-boot-statistics/?tab=reviews
