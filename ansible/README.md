> [!IMPORTANT]
> If You Want To Run My JenkinsFile Properly You Need At Least **jenkins** **gitlab-pkg** **nexus** **defectdojo** **vault**

## Monitoring

- falco `Optional`
+ fluent-bit `Optional`
* cadvisor (Monitor Docker Service Resource)`Optional`
- falco_sidekik`Optional`
+ prometheus`Optional`
* filebeat`Optional`
- grafana`Optional`
+ logstash`Optional`
* node_exporter`Optional`

### Logging: 

- elastic`Optional`
+ kibana`Optional`

### CI/CD:

+ gitlab-pkg
- jenkins-pkg`Optional`
* jenkins
- jenkins-agent`Optional`

### Postgresql:

- etcd`Optional`
+ patroni`Optional`

### Other Services 

- lvm (Detect All 80% Usage Disk And Resize It Only Works When The Vg And Lv Seprate by _ Not -)`Optional`
* zabbix-agent (Install Zabbix Agent By Service Discovery) `Optional`
+ sonarqube (Check Code)`Optional`
* zap (Security Scan) `Optinal`
- k3s_ansible (Install k3s Cluster)`Optinal`
+ rsyslog ()`Optinal`
- defectdojo (Centeralize Report)
+ requirment (Install Docker & Create Network Seprated On Docker And Put Log And Rotate On daemon.json)
* vault (Config Valut)
- nexus (Local Registery)

