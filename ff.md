# 🚀 Hamza Advanced App

Ce projet est une application Node.js dockerisée et déployée dans un environnement Kubernetes avec une structure claire et des bonnes pratiques DevOps.

---

## ✅ Fonctionnalités principales

- 🐳 Dockerfile (Node.js 18)
- 📦 App.js avec fichier .env
- 🔐 Déploiement Kubernetes avec Secrets, ConfigMap, Namespace
- 🧱 MongoDB avec Persistent Volume
- 🌐 Ingress NGINX avec domaine personnalisé (hamza.local)
- 📁 Arborescence claire : app/, k8s/, dbmongo/

---

## 🎯 Objectif

Ce projet simule un déploiement cloud complet en local, idéal pour les environnements DevOps réels ou à des fins de formation.

---

## 📁 Structure du projet
```bash
hamza-advanced-app/
├── app/ # Code source Node.js
│ ├── app.js
│ ├── package.json
│ └── Dockerfile
├── dbmongo/ # Manifeste MongoDB
│ ├── mongo-deployment.yaml
│ └── mongo-service.yaml
├── k8s/ # Déploiement Kubernetes App
│ ├── configmap.yaml
│ ├── deployment.yaml
│ ├── ingress.yaml
│ ├── namespace.yaml
│ ├── secret.yaml
│ └── service.yaml
└── README.md
```
---

## 🧪 Déploiement local avec Kubernetes (Minikube ou Docker Desktop)

> ⚠ Assurez-vous que Kubernetes est activé et que l’Ingress Controller (comme NGINX) est installé.
## Installer l’Ingress Controller NGINX (si ce n’est pas déjà fait)
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.10.0/deploy/static/provider/cloud/deploy.yaml
## Vérifier que tout fonctionne
```bash
kubectl get all -n ingress-nginx
kubectl get ingress
```

### 🧱 1. Créer le namespace
```bash
kubectl apply -f k8s/namespace.yaml
```
## 🗃 2. Déployer MongoDB
```bash
kubectl apply -f dbmongo/
```
## 🚀 3. Déployer l’application Node.js
```bash
kubectl apply -f k8s/
```
## 🌐 Accès à l’application
✅ Option A – Accès via Ingress (domaine personnalisé)

Ajoutez la ligne suivante ( 127.0.0.1 hamza.local )à votre fichier hosts :
Système	              Fichier
Linux/macOS	           /etc/hosts
Windows	               C:\Windows\System32\drivers\etc\hosts

## Accédez à l’application :
http://hamza.local

✅ Option B – Accès via port-forwarding
```bash
kubectl port-forward svc/hamza-service 8080:80 -n hamza-project
```
## Puis accédez à :
http://localhost:8080

## 🧰 Vérification & debug
```bash
kubectl get pods -n hamza-project
kubectl get svc -n hamza-project
kubectl logs -f deployment/hamza-app -n hamza-project 
```
👨‍💻 Auteur
Hamza Hssaini
[📎 LinkedIn](https://www.linkedin.com/in/hamza-hssaini-149a9b310)

📜 Licence
Ce projet est open source, vous pouvez le réutiliser, le modifier et le partager à des fins éducatives.
