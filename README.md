# recosante_exporter

```sh
docker-compose up -d
```

Prometheus configuration
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
