# TP Monitoring - Spring Boot Actuator + Prometheus + Grafana

## Description du Projet
Ce TP vise à doter une application Spring Boot de capacités de supervision, journalisation et monitoring comparables à celles utilisées en production dans les environnements DevOps modernes.

##  Objectifs
- Collecter des indicateurs de performance via Spring Boot Actuator
- Exporter les données vers Prometheus pour une collecte centralisée  
- Visualiser dynamiquement ces métriques dans Grafana
- Mettre en œuvre une journalisation structurée et configurable

##  Architecture du Système
```
Spring Boot App (8080) → Prometheus (9090) → Grafana (3000)
      ↓
   Actuator Metrics
      ↓
  Logs Structurés
```

##  Structure du Projet
```
tp15-monitoring/
├── src/main/java/ma/ens/tp15monitoring/
│   ├── Tp15MonitoringApplication.java
│   ├── controller/
│   │   └── DemoController.java
│   ├── service/
│   │   └── DemoService.java
│   └── config/
│       └── InfoConfig.java
├── src/main/resources/
│   └── application.properties
├── monitoring-tools/
│   ├── prometheus/
│   │   └── prometheus.yml
│   └── grafana/
└── logs/
    └── tp15-application.log
```

##  Configuration

### Spring Boot Actuator
```properties
management.endpoints.web.exposure.include=*
management.endpoint.health.show-details=always
management.metrics.export.prometheus.enabled=true
```

### Métriques Personnalisées
```properties
info.app.name=TP15 Monitoring Application
info.app.version=1.0.0
info.app.description=Supervision avec Actuator + Prometheus + Grafana
```

##  Démarrage de l'Application

### 1. Application Spring Boot
```bash
cd tp15-monitoring
mvn spring-boot:run
```

### 2. Prometheus
```bash
cd monitoring-tools/prometheus
.\prometheus.exe --config.file=prometheus.yml
```

### 3. Grafana
```bash
cd monitoring-tools/grafana/bin
.\grafana-server.exe
```

##  Endpoints Disponibles

### Application
- `http://localhost:8080/process` - Traitement de données
<img width="1917" height="967" alt="image" src="https://github.com/user-attachments/assets/0852b505-5409-41e6-af37-ac56be37a1cb" />

- `http://localhost:8080/hello` - Endpoint simple

  <img width="1916" height="968" alt="image" src="https://github.com/user-attachments/assets/f7995328-945b-4c89-af63-5d5c2fd91436" />

- `http://localhost:8080/error-sim` - Simulation d'erreur
  

### Monitoring
- `http://localhost:8080/actuator/health` - Santé de l'application
  <img width="1918" height="825" alt="image" src="https://github.com/user-attachments/assets/66b82458-134e-4e41-9d23-5ac3e58c73a2" />

- `http://localhost:8080/actuator/info` - Informations personnalisées
  <img width="1913" height="755" alt="image" src="https://github.com/user-attachments/assets/e41d56ea-71c5-40d8-9006-60d12b11030b" />

- `http://localhost:8080/actuator/prometheus` - Métriques Prometheus
  

https://github.com/user-attachments/assets/0eaa8b89-5afa-43a0-9fcf-748d1e8a3b35


- `http://localhost:9090` - Interface Prometheus
  <img width="1918" height="977" alt="image" src="https://github.com/user-attachments/assets/d5619a76-d74b-4098-82dc-f23b760ec54c" />

- `http://localhost:3000` - Interface Grafana
<img width="1917" height="972" alt="image" src="https://github.com/user-attachments/assets/5d405d1e-700f-4dc2-97be-270734b02927" />




### Vérifications
-  Application Spring Boot démarre sur le port 8080
-  Actuator expose les endpoints de monitoring
-  Prometheus scrape les métriques
-  Grafana connecté à Prometheus
-  Dashboard affiche les données en temps réel


## Démonstration


### Dashboard Grafana


https://github.com/user-attachments/assets/e5b0f947-e266-4c70-bf13-36878c615648


### Métriques Prometheus
<img width="1918" height="966" alt="image" src="https://github.com/user-attachments/assets/411478f4-d0be-4072-89fd-9227eecc888c" />

### Logs de l'Application


https://github.com/user-attachments/assets/5c581f7b-ec7d-4eba-8206-4de0608aad83


##  Compétences Acquises

-  Configuration de Spring Boot Actuator
-  Export des métriques vers Prometheus
-  Création de dashboards Grafana
-  Journalisation structurée
-  Surveillance des performances JVM
-  Monitoring des requêtes HTTP
-  Mise en place d'une chaîne complète d'observabilité

##  Encadrement & réalisation

---

**Réalisée par** : BENZIAT hana
<br>
**Encadré par** : Mr.LACHGAR mohammed
<br>
**Gmail** : h.benziat1318@uca.ac.ma
