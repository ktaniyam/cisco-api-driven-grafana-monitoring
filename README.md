<img src="https://img.shields.io/badge/Cisco-1BA0D7.svg?style=popout&logo=Cisco&logoColor=white"> <img src="https://img.shields.io/badge/-Grafana-F46800.svg?logo=grafana&style=popout"> ![InfluxDB](https://img.shields.io/badge/InfluxDB-22ADF6?style=flat&logo=InfluxDB&logoColor=white) <img src="https://img.shields.io/badge/-Python-3776AB.svg?logo=python&style=popout"> [![published](https://static.production.devnetcloud.com/codeexchange/assets/images/devnet-published.svg)](https://developer.cisco.com/codeexchange/github/repo/kaisero/fireREST)

# Cisco Api-driven Grafana Monitoring
Unleashing the Power of Cisco Observability: API-Driven Insights on a Single Dashboard

This project harnesses the potential of Cisco's observability products by leveraging the APIs of [SD-WAN](https://www.cisco.com/site/us/en/solutions/networking/sdwan/index.html), [Catalyst Center](https://www.cisco.com/site/us/en/products/networking/catalyst-center/index.html), [Meraki](https://meraki.cisco.com/), and [ThousandEyes](https://www.thousandeyes.com/). By seamlessly integrating data from these diverse sources, we create a unified dashboard that provides comprehensive visibility and insights into your network.

Through the power of APIs, we break down silos and bring together critical information from multiple domains. Whether it's SD-WAN performance metrics, Catalyst Center analytics, Meraki network health, or ThousandEyes real-user monitoring data, our dashboard presents a holistic view of your infrastructure.

Our goal is to empower network administrators, IT teams, and decision-makers with the tools they need to monitor, troubleshoot, and optimize their networks effectively. By leveraging the rich capabilities of Cisco's observability products and the flexibility of Grafana, we deliver a solution that is both powerful and user-friendly.

Join us in this exciting journey as we revolutionize network observability and unlock new possibilities through API-driven insights. Together, we can create a more connected, efficient, and resilient world.

## Preview

<p align="center">
  <img width = "400" height = "207" alt="Screenshot 2024-04-05 at 14 49 08" src="https://github.com/uzumal/cisco-api-driven-grafana-monitoring/blob/main/images/preview-1.png?raw=true">
  <img width = "400" height = "207"　alt="Screenshot 2024-04-05 at 14 49 46" src="https://github.com/uzumal/cisco-api-driven-grafana-monitoring/blob/main/images/preview-2.png?raw=true">
  <img width = "400" height = "207" alt="Screenshot 2024-04-05 at 14 50 01" src="https://github.com/uzumal/cisco-api-driven-grafana-monitoring/blob/main/images/preview-3.png?raw=true">
  <img width = "400" height = "207" alt="Screenshot 2024-04-05 at 14 50 01" src="https://github.com/uzumal/cisco-api-driven-grafana-monitoring/blob/main/images/preview-4.png?raw=true">
</p>

## Contributors

<div align = "center">
  <table>
    <tr>
      <td align="center"　style="margin-left: auto; margin-right: auto;">
        <a href="https://github.com/uzumal">
          <img src="https://github.com/uzumal.png" width="100" height="100" style="border-radius:50%">
          <br />
          Kazuma Takeuchi
        </a>
      </td>
      <td align="center">
        <a href="https://github.com/baskei0130">
          <img src="https://github.com/baskei0130.png" width="100" height="100" style="border-radius:50%">
          <br />
          Keita Shimada
        </a>
      </td>
      <td align="center">
        <a href="https://github.com/ktaniyam">
          <img src="https://github.com/ktaniyam.png" width="100" height="100" style="border-radius:50%">
          <br />
          Katsutoshi Taniyama
        </a>
      </td>
    </tr>
  </table>
</div>

## Usage
> [!NOTE]
> To automate the execution of the Python scripts and reflect the changes in Grafana, you can utilize the provided shell scripts in the run-script directory. Follow these steps:
1. Open a new tmux session for each script:

```console
tmux new-session -s dnac
tmux new-session -s meraki
tmux new-session -s thousandeyes
tmux new-session -s sdwan
```

2. In each tmux session, navigate to the run-script directory and execute the corresponding shell script with sudo permissions:

```console
cd run-script
sudo ./run_dnacMain.sh
sudo ./run_merakiMain.sh
sudo ./run_teMain.sh
sudo ./run_sdwanMain.sh
```

By running these shell scripts, the associated Python scripts will be automatically executed, and the collected data will be seamlessly integrated into Grafana. This streamlined approach ensures that your Grafana dashboard stays up to date with the latest information from the Cisco platforms.

## Prerequisites
Before proceeding with the project, ensure that you have completed the following tasks:

### Environment Setup

- [ ] Install and configure [Grafana](https://github.com/grafana/grafana)
- [ ] Install and set up [InfluxDB](https://github.com/influxdata/influxdb)

### Cisco Platforms
> [!NOTE]
> The Catalyst Center, SDWAN versions shown here are only those used in this environment.

#### SDWAN

- [ ] Provision and configure SDWAN environment
- cEdge: 17.05.01
- vManage: 20.5.1
- vBond: 20.5.1
- vSmart: 20.5.1

#### ThousandEyes

- [ ] Set up ThousandEyes account and configure necessary tests

#### Meraki

- [ ] Configure Meraki dashboard and devices

#### Catalyst Center

- [ ] Install and configure Catalyst Center VM
- Version: 2.3.7.5

Once you have completed these prerequisites, you'll be ready to dive into the main project!
> [!WARNING]
> Different versions running may result in APIs that are no longer available

## Directory Structure
<pre>
.
├── dnac-esxi-prod
│   ├── __pycache__
│   ├── dnacApis.py
│   └── dnacMain.py
├── meraki
│   ├── __pycache__
│   ├── change_env.sh
│   ├── const.py
│   ├── influxdbApis.py
│   ├── merakiApis.py
│   ├── merakiMain.py
│   └── venv
├── run-script
│   ├── change_env.sh
│   ├── run_dnacMain.sh
│   ├── run_merakiMain.sh
│   ├── run_teMain.sh
│   └── run_sdwanMain.sh
├── thousandeyes
│   ├── teMain.py
│   ├── teApis.py
│   └── data_processing.py
├── sdwan-cml-prod
│   ├── __pycache__
│   ├── sdwanApis.py
└── └── sdwanMain.py
</pre>

## Environment Variables
```shell
# .env for Catalyst Center 
DNAC_USERNAME=
DNAC_PASSWORD=
DNAC_HOST=

# .env for Catalyst SDWAN
SDWAN_USERNAME=
SDWAN_PASSWORD=
SDWAN_HOST=

# .env for Meraki
MERAKI_API_KEY=

# .env for ThousandEyes
TE_TOKEN=

# .env for ThousandEyes Proxy
HTTP_PROXY=
HTTPS_PROXY=
```
