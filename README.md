# mysql-monitoring

Monitoring MYSQL with grafana-prometheus

1. Installing & Configuring the Prometheus Server
Install with docker
2. Create Prometheus Exporter Database User

        CREATE USER 'mysqld_exporter'@'%' IDENTIFIED BY 'StrongPassword' WITH MAX_USER_CONNECTIONS 2;
        ALTER USER 'mysqld_exporter'@'%' IDENTIFIED WITH mysql_native_password BY 'StrongPassword';
        GRANT PROCESS, REPLICATION CLIENT, SELECT ON *.* TO 'mysqld_exporter'@'%';
        FLUSH PRIVILEGES;

3. Prometheus MySQL Exporter use docker-compose.yaml

        change export to your owned value
4. Configure MySQL Endpoint to be Scraped by Prometheus

        scrape_configs:
          [...]
          - job_name: 'mysql_exporter'
            static_configs:
              - targets:
                - "192.168.132.18:9104"
5. Creating Dashboards

        https://grafana.com/grafana/dashboards/7362