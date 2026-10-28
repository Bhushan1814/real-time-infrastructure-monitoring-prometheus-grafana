# Real-Time Infrastructure Monitoring and Alerting using Prometheus and Grafana on AWS EC2

## Project Overview

This project implements a real-time infrastructure monitoring and alerting solution using Amazon EC2, Prometheus, Node Exporter, and Grafana.

Prometheus collects infrastructure metrics, Node Exporter exposes Linux system metrics, and Grafana visualizes monitoring data through dashboards. Alert rules can be configured to identify high CPU utilization and other infrastructure issues.

## Objectives

- Monitor Linux EC2 instances in real time.
- Collect CPU, memory, disk, and system metrics.
- Visualize infrastructure performance through Grafana dashboards.
- Configure Prometheus alert rules.
- Test monitoring and alert behavior.
- Practice AWS, Linux, and DevOps monitoring concepts.

## Technologies Used

- AWS EC2
- Ubuntu Linux
- Prometheus
- Node Exporter
- Grafana
- PromQL
- YAML
- Linux commands and systemd

## Architecture

The monitoring architecture consists of one monitoring server and two target application servers.

1. Node Exporter runs on each target EC2 instance.
2. Prometheus scrapes metrics from the target instances.
3. Grafana queries Prometheus for dashboard visualizations.
4. Prometheus evaluates configured alert rules.

Add your architecture diagram here:

`![Monitoring Architecture](architecture/monitoring-architecture.png)`

## Infrastructure

| Component | Purpose |
|---|---|
| Monitoring EC2 | Runs Prometheus and Grafana |
| Application EC2 1 | Exposes Linux metrics using Node Exporter |
| Application EC2 2 | Exposes Linux metrics using Node Exporter |
| Prometheus | Collects and stores time-series metrics |
| Grafana | Displays monitoring dashboards |

## Implementation Steps

1. Launch three Ubuntu EC2 instances.
2. Configure security groups and network connectivity.
3. Install Node Exporter on both target servers.
4. Install and configure Prometheus on the monitoring server.
5. Add the target instances to Prometheus scrape configuration.
6. Verify targets are reporting as UP.
7. Install Grafana and configure Prometheus as a data source.
8. Create dashboards for CPU, memory, disk, and system performance.
9. Configure alert rules for high CPU utilization.
10. Generate test load and verify the alert behavior.

## Monitoring and Alerting

Example PromQL query for CPU utilization:

```promql
100 * (1 - avg by (instance) (
  rate(node_cpu_seconds_total{mode="idle"}[5m])
))
```

Example alert condition: CPU utilization above 70% for five minutes. Configure the rule and its notification mechanism according to your deployment.

## Screenshots

Add your actual screenshots to the `screenshots/` directory.

- Prometheus targets status
- Grafana infrastructure dashboard
- CPU utilization graph
- Memory and disk metrics
- CPU alert rule and test result

## Security Considerations

- Restrict SSH access to trusted IP addresses.
- Allow Prometheus access to Node Exporter only from the monitoring server.
- Restrict Grafana access to authorized users and networks.
- Do not upload AWS credentials, private keys, passwords, or sensitive infrastructure details.

## Learning Outcomes

- AWS EC2 instance provisioning
- Linux server administration
- Prometheus installation and configuration
- Node Exporter metrics collection
- Grafana dashboards and PromQL
- Infrastructure alerting and troubleshooting
- Basic cloud monitoring security

## Future Enhancements

- Configure Alertmanager and email notifications.
- Automate deployment using Ansible.
- Provision monitoring infrastructure using Terraform.
- Add more application and infrastructure metrics.
- Integrate monitoring into a broader CI/CD workflow.

## Author

**Bhushan Jagtap**

Aspiring AWS Cloud / DevOps Engineer

GitHub: https://github.com/Bhushan1814

LinkedIn: https://www.linkedin.com/in/bhushansjagtap

---

*This repository documents the project setup, configuration, testing, and results. Update the documentation with verified deployment details and actual screenshots before publishing.*
