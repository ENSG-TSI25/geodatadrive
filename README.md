# TSIC 2026 - Déploiement

## Prérequis
- Jump server : `tsic2026.duckdns.org`

---

## 1. Connexion
```bash
ssh node01
```

---

## 2. Initialisation du réseau partagé
> À exécuter **une seule fois** depuis un manager.

---

## 3. Déploiement des stacks

### Load Balancer (Traefik)
```bash
docker stack deploy -c lb.yaml lb
```

### Monitoring (Prometheus + Grafana + cAdvisor + node_exporter)
```bash
docker stack deploy -c monitoring.yaml monitoring
```

### Application (Nextcloud + OnlyOffice + MariaDB Galera + Redis)
```bash

# 1. Déployer la stack applicative
docker stack deploy -c app.yaml cloud

# 2. Démarrer le seed MariaDB (initialisation du cluster)
docker service scale cloud_db=2
# Attendre ~30s que le cluster soit initialisé, puis :
docker service scale cloud_seed=0
docker service scale cloud_db=3
docker service scale cloud_nextcloud=1
```

---
## 4. Vérifications
```bash
# État des stacks
docker stack ls

# État des services
docker service ls

# Logs d'un service
docker service logs 

# Nœuds du cluster Swarm
docker node ls
```

---

## 5. Accès
| Service    | URL                                      |
|------------|------------------------------------------|
| Nextcloud  | http://nextcloud.tsic2026.duckdns.org    |
| OnlyOffice | http://onlyoffice.tsic2026.duckdns.org   |
| Grafana    | http://grafana.tsic2026.duckdns.org      |
| Traefik    | http://lb.tsic2026.duckdns.org           |

Grafana : `admin` / `admin`  
Nextcloud : `user` / voir `app.yaml`

---

## 6. Mise à l'échelle
```bash
# Exemple : scaler Nextcloud à 2 ou 3 replicas
docker service scale cloud_nextcloud=2
```

---

## 7. Suppression
```bash
docker stack rm cloud
docker stack rm monitoring
docker stack rm lb
```
