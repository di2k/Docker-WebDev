# Docker-WebDev 

Docker-compose untuk pengembangan web dengan multiple PHP, database, dan monitoring tool.

## Komponen

### Web Services
- **Nginx**: Web server (Port 80, 443)
- **PHP**: Multiple versions (7.4, 8.0, 8.3)

### Databases
- **MariaDB**: MySQL-compatible DB (Port 3307)
  - Root Password: rootpassword
  - Default DB: exampledb
  - Default User: exampleuser
  - Default Pass: examplepass

- **MongoDB**: NoSQL Database (Port 27017)

- **PostgreSQL** (Port 5432)
  - Default DB: exampledb
  - Default User: exampleuser
  - Default Pass: examplepass

### Search & Analytics
- **Elasticsearch**: Search engine (Port 9200, 9300)
  - Password: changeme
  - Memory: 512MB (Xms & Xmx)

- **Kibana**: Elasticsearch UI (Port 5601)

### Monitoring
- **Grafana**: Analytics & monitoring (Port 4124)
  - Username: admin
  - Password: grafanapass

### IoT Stack
- **Mosquitto**: MQTT Broker (Port 1883)
- **InfluxDB**: Time series database (Port 8086)
  - Username: admin
  - Password: influxpass
  - Organization: myorg
  - Default Bucket: sensors
- **Telegraf**: Metrics collector

## Volume Mounts
- **/nginx**: Konfigurasi Nginx
- **/html**: Root direktori web
- **/ssl**: SSL certificates
- **/db_data**: Dara MariaDB
- **/mosquitto**: Konfigurasi dan data MQTT
