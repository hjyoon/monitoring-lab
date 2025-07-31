# monitoring-lab

A minimal setup for server and system monitoring using **Prometheus**, **Grafana**, and **Node Exporter** with Docker Compose.

## Features

- **Node Exporter** collects host-level hardware and OS metrics.
- **Prometheus** scrapes and stores metrics.
- **Grafana** visualizes metrics with pre-provisioned dashboards and data sources.

## Quick Start

```sh
docker compose up -d
```

### Access

- Prometheus: [http://localhost:9090](http://localhost:9090)
- Grafana: [http://localhost:3000](http://localhost:3000)  
  (Default login: `admin` / `admin`)

## Notes

- `network_mode: "host"` and `pid: "host"` in `node-exporter` allow direct access to the host’s network and process information.
- Volumes such as `/run/systemd` and `/run/dbus/system_bus_socket` are needed for advanced metrics like systemd services.
- Adjust `targets` in `prometheus.yml` according to your host network configuration. `172.17.0.1` is the default Docker bridge IP for the host.
- Dashboards and data sources are automatically provisioned at container startup.
- Place your Grafana dashboard JSON files in `grafana/dashboards/` to auto-import them.

## Example Dashboard

Below is an example of the Grafana dashboard you'll see after setup:

<img width="1985" height="1895" alt="Image" src="https://github.com/user-attachments/assets/91365d94-3306-49bd-9505-e5c42a2d6e12" />

The default Grafana dashboard is based on:  
[Node Exporter Full - Grafana Dashboard 1860](https://grafana.com/grafana/dashboards/1860-node-exporter-full/)
