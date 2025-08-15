# Grafana Dashboard for GenLayer Validator

A ready-to-use Grafana dashboard to monitor a **GenLayer validator node** using **Prometheus** and the **Infinity datasource plugin**.  
It provides visibility into validator status, synchronization, block metrics, transaction metrics, and system performance (CPU, RAM, Disk, GC, Network).

<img width="2174" height="1187" alt="gen_layer_validator_dashboard" src="https://github.com/user-attachments/assets/047e95c6-b685-41f9-9539-379199bd3d76" />

## Requirements

- **Grafana** (tested on 11.x)
- **Prometheus**
- **yesoreyeram-infinity-datasource** plugin for Grafana
- A GenLayer validator node exposing:
  - Prometheus metrics (with `genvm`, `webdriver`, `node` collectors)
  - HTTP health endpoint: `http://<instance_ip>:<metrics_port>/health` with JSON containing `checks.validating.status`

## Dashboard Variables

- `instance_ip` — IP address of the GenLayer node
- `metrics_port` — Prometheus metrics port (default: `9153`)

## Notes

- Ensure the node’s metrics and health endpoints are reachable from both Grafana and Prometheus.
- The health status panel relies on the **Infinity** datasource parsing JSON from `/health`.
- Some panels display external images — replace them with local assets if required.
- Thresholds for **CPU**, **RAM**, and **Disk** usage are generic and can be adjusted.

> ⚠️ **Important:** After importing the dashboard, manually re-select the **Infinity** datasource for the `"Validator"` panel (top-left).
> Grafana might incorrectly assign the default **Prometheus** datasource.
>To fix:
>1. Edit the panel → go to **Panel settings** → **Datasource**
>2. Select the correct **Infinity** datasource from the dropdown
>3. Ensure the URL is correctly set as:  
   `http://$instance_ip:$metrics_port/health`
<img width="1389" height="459" alt="gen_layer_validator_dashboard_query" src="https://github.com/user-attachments/assets/c2a5f0b4-a6f0-4be2-abb7-f2991bc27581" />

##

<img src="https://www.5elementsnodes.com/wp-content/uploads/2023/12/LOGO-1.png" width="25%">
