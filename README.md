# TODO List Infrastructure - Docker Compose - Projet exam

## Description
Cette infrastructure met en place une application de gestion de tâches avec :
- API REST (Flask ou Node.js)
- Base de données PostgreSQL
- Monitoring (Prometheus, Grafana)
- Reverse proxy (Traefik)

## Architecture

```
[ Client Web ]
     |
     v
[ Traefik Reverse Proxy ]
     |
+----+----+
|         |
v         v
API     Grafana
 |         ^
 v         |
DB <--> Prometheus
 |         ^
 v         v
Postgres Exporter / Node Exporter
```

## Services
- `app` : Application métier REST (Flask/Node.js)
- `db` : PostgreSQL
- `traefik` : Reverse proxy
- `prometheus` : Monitoring
- `grafana` : Dashboards
- `postgres_exporter` & `node_exporter` : Exportateurs de métriques

## Structure
```
todo-docker-infra/
├── README.md
├── .env.example
├── docker-compose.yml
├── app/
│   ├── Dockerfile
│   ├── main.py (ou index.js)
│   ├── requirements.txt (ou package.json)
│   └── config/
│       └── database.py
├── traefik/
│   └── traefik.yml
├── prometheus/
│   └── prometheus.yml
├── grafana/
│   ├── provisioning/
│   │   ├── dashboards/
│   │   └── datasources/
│   └── dashboards/
└── scripts/
    └── init-db.sql
```

## Lancement
```bash
docker-compose up -d
```

## Réalisé par
Tchoudji Silvere