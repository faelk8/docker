


<h1 align="center">
  <img src="image/prometheus.png" alt="Prometheus" width=120px height=120px >
  <br>
  Docker Prometheus 
</h1>

<div align="center">

[![Status](https://img.shields.io/badge/version-1.0-blue)]()
![Static Badge](https://img.shields.io/badge/status-desenvolvimento-deve)

</div>

# Prometheus
Código do Promethues

docker-compose.yaml
```
  prometheus:
    image: prom/prometheus
    container_name: prometheus
    depends_on: 
      - cadvisor
    ports:
      - 9090:9090
    command:
      - --config.file=/etc/prometheus/prometheus.yml
    volumes:
      - ./prometheus.yml:/etc/prometheus/prometheus.yml:ro
```
* No volumes substitui o arquivos promethues.yml do container pelo prometheus.yml da minha pasta atual.

Arquivos de configuração do monitoramento.

prometheus.yml
```
  global:
    scrape_interval:     15s 
    evaluation_interval: 15s 

  rule_files:

  scrape_configs:
    - job_name: 'prometheus'
      scrape_interval: 5s
      static_configs:
        - targets: ['localhost:9090']
```
**targets**  onde vai ser observado.

http://localhost:9090


# CadAdivisor
Monitora

docker-compose.yaml
```
  cadvisor:
    image: gcr.io/cadvisor/cadvisor:latest
    container_name: cadvisor
    user: root
    ports:
    - 8080:8080
    volumes:
    - /:/rootfs:ro
    - /var/run:/var/run:rw
    - /sys:/sys:ro
    - /var/run/docker.sock:/var/run/docker.sock
    depends_on:
    - redis
```

prometheus.yml
```
...
scrape_configs:
  - job_name: cadvisor
    scrape_interval: 5s
    static_configs:
    - targets:
      - cadvisor:8080
```
http://localhost:8080

# Grafana
docker-compose.yaml
```
  grafana:
    image: grafana/grafana
    ports:
      - "3000:3000"
    container_name: grafana
    depends_on:
      - prometheus

  redis:
    image: redis:latest
    container_name: redis
    ports:
    - 6379:6379      
```


#






