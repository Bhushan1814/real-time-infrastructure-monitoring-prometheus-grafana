# Linux Commands – Prometheus and Grafana Monitoring

## System Information

```bash
hostname
hostname -I
uptime
free -h
df -h
top
```

## Check Node Exporter

```bash
sudo systemctl status node_exporter
sudo systemctl enable node_exporter
sudo systemctl restart node_exporter
```

Check metrics locally:

```bash
curl http://localhost:9100/metrics
```

## Check Prometheus

```bash
sudo systemctl status prometheus
sudo systemctl restart prometheus
```

Validate the configuration using the installed Prometheus binary and its actual configuration path:

```bash
promtool check config /etc/prometheus/prometheus.yml
```

## Check Grafana

```bash
sudo systemctl status grafana-server
sudo systemctl restart grafana-server
```

## Troubleshooting

```bash
sudo journalctl -u prometheus -n 50 --no-pager
sudo journalctl -u node_exporter -n 50 --no-pager
sudo journalctl -u grafana-server -n 50 --no-pager
```

**Note:** Service names, installation paths, and configuration paths may differ depending on the installation method. Verify them on your EC2 instances.
