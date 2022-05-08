# recosante_exporter

## Quickstart

Commands to start the exporter:
```sh
git clone https://github.com/antoinbo/recosante_exporter.git
cd recosante_exporter
docker-compose up -d
```

Prometheus configuration to scrape the exported values:
```yaml
scrape_configs:

  - job_name: json_exporter
    static_configs:
      - targets: ["recosante_exporter:7979"]

  - job_name: recosante_exporter
    scrape_interval: 6h
    metrics_path: /probe
    params:
      target: ["https://api.recosante.beta.gouv.fr/v1/?insee=75056&show_raep=true&show_indice_uv=true"]
    static_configs:
      - targets: ["recosante_exporter:7979"]
```

## Demo with Prometheus + Grafana

This example is meant to setup a quick environment to test the project, it is not secured and it must not be used in production without a proper security configuration.

Commands to start the demo:
```sh
git clone https://github.com/antoinbo/recosante_exporter.git
cd recosante_exporter/examples
docker-compose up -d
```

Open the Grafana console on your web browser: https://localhost:3000/

Command to end the demo:
```sh
docker-compose down
```
