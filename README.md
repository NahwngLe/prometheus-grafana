# 📊 Prometheus & Grafana Monitoring Stack

A ready-to-use monitoring stack that integrates **Prometheus** and **Grafana** via Docker Compose. This setup allows you to collect, store, and visualize metrics from your applications or infrastructure efficiently.

## 🚀 Features

* 📆 **Dockerized Setup**: Quick deployment with Docker Compose.
* 📈 **Prometheus**: Time-series database for collecting metrics.
* 📊 **Grafana**: Interactive dashboards for data visualization.
* 🔧 **Pre-configured Dashboards**: Easily import or customize dashboards.
* 🛠️ **Extensible**: Add exporters like Node Exporter, cAdvisor, or custom metrics endpoints.

## 📁 Project Structure

```
prometheus-grafana/
├── docker-compose.yml
├── prometheus/
│   └── prometheus.yml
├── grafana/
│   └── provisioning/
│       ├── datasources/
│       │   └── datasource.yml
│       └── dashboards/
│           └── dashboard.json
└── README.md
```

## 🧰 Prerequisites

* **Docker** installed on your machine.
* **Docker Compose** installed.

## ⚙️ Setup Instructions

1. **Clone the Repository**

   ```bash
   git clone https://github.com/NahwngLe/prometheus-grafana.git
   cd prometheus-grafana
   ```

2. **Start the Services**

   ```bash
   docker-compose up -d
   ```

   This command will:

   * Launch Prometheus on [http://localhost:9090](http://localhost:9090)
   * Launch Grafana on [http://localhost:3000](http://localhost:3000)

3. **Access Grafana**

   * Navigate to [http://localhost:3000](http://localhost:3000) in your browser.
   * **Default Credentials**:

     * Username: `admin`
     * Password: `admin`
   * Upon first login, you'll be prompted to change the password.

4. **Import Dashboards**

   * In Grafana, go to **"Dashboards" > "Import"**.
   * You can import pre-configured dashboards from the `grafana/provisioning/dashboards/` directory or create your own.

## 📡 Adding Exporters

To monitor specific services or system metrics, you can add exporters:

* **Node Exporter**: For system-level metrics.
* **cAdvisor**: For container metrics.
* **Custom Exporters**: For application-specific metrics.

Update the `prometheus.yml` configuration file to include the new exporters:

```yaml
scrape_configs:
  - job_name: 'node_exporter'
    static_configs:
      - targets: ['node-exporter:9100']
```

Ensure the exporter containers are running and accessible to Prometheus.

## 🪯 Stopping and Cleaning Up

To stop the services:

```bash
docker-compose down
```

To remove all containers, networks, and volumes:

```bash
docker-compose down --volumes
```

## 📄 License

This project is licensed under the [MIT License](LICENSE).

## 🤝 Contributing

Contributions are welcome! Please fork the repository and submit a pull request for any enhancements or bug fixes.

## 📬 Contact

For any questions or suggestions, feel free to open an issue or contact [NahwngLe](https://github.com/NahwngLe).
