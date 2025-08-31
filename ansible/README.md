### Suported Services
Support Monitoring, Logging, Postgresql, Agents, Repository, CI/CD
> [!IMPORTANT]
> If You Want To Run My JenkinsFile Properly You Need At Least **jenkins** **gitlab-pkg** **nexus** **defectdojo** **vault**

## Monitoring
```
falco 
fluent-bit 
cadvisor (Monitor Docker Service Resource)
falco_sidekik
prometheus
filebeat
grafana
logstash
node_exporter
```
### Logging: 
```
elastic
kibana
```
### CI/CD:
```
gitlab-pkg
jenkins-pkg
jenkins
jenkins-agent
```
### Postgresql:
```
etcd
patroni
```
### Other Services 

- lvm (Detect All 80% Usage Disk And Resize It Only Works When The Vg And Lv Seprate by _ Not -)<sup> Optional </sup>
+ rsyslog ()
* zabbix-agent (Install Zabbix Agent By Service Discovery) `Optional`
- nexus (Local Registery)
+ sonarqube (Check Code)`Optional`
* zap (Security Scan) `Optinal`
- defectdojo (Centeralize Report)
+ requirment (Install Docker & Create Network Seprated On Docker And Put Log And Rotate On daemon.json)
* vault (Config Valut)
- k3s_ansible (Install k3s Cluster)`optinal`

