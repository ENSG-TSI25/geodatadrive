# geodatadrive

Pour l'accès aux serveurs ; https://drive.ird.fr/s/tsic2026 dans le fichier instructions.md

Faire les étapes d'installation de la clef ssh et de configuration.
Faire `ssh node01` pour tester l'installation. Si une passphrase est demandée, rentrez `docker`.


# Monitoring 

### Docker file

Fichier à modifier : docker-compose.yaml 
Potentiellement prometheus.yaml à modifier pour paramétrer grafana

### Déployement 

prometheus node01 :

```bash
docker stack deploy <name>
```

### Liens utiles 
```bash
https://grafana.com/docs/grafana/latest/fundamentals/getting-started/first-dashboards/get-started-grafana-prometheus/

https://hub.docker.com/r/grafana/grafana
```


```bash
https://docs.docker.com/reference/cli/docker/stack/deploy/

```


```bash
https://prometheus.io/docs/prometheus/latest/configuration/configuration/#dns_sd_config

https://prometheus.io/docs/guides/node-exporter/

https://prometheus.io/docs/prometheus/latest/getting_started/
```

