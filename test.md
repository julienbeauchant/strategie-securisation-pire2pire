# Stratégie de sécurisation de l'application pire2pire

## 1. Introduction
**pire2pire** est une plateforme de formation en ligne pour les formateurs et les apprenants.
Elle vise à une stratégie de sécurisation qui couvrent divers aspects de la sécurité, conformément aux exigences, de conformité, d'expérience utilisateur et de protection contre les menaces.

## 2. Règles d'Hygiène de Sécurité

### 2.1 RGPD
- **Réglementation du RGPD** : 
Le RGPD est une Règlementation de l’Union Européenne pour protéger la vie privé des individus et réguler le traitement de données personnelles avec des mécansimes de gestion de consentement.

### 2.2 Défense en profondeur
- **Multi-couches de sécurité** : 
La défense en profondeur est une stratégie de sécurité multi-couches afin de protéger l'application en cas de faille.

### 2.3 Moindre privilège
- **Utilisation du RBAC** : 
N'octroyer qu'aux éléments acteurs de l'application, les permissions strictement nécessaires en définissant des rôles.

## 3. Back-End

### 3.1 Base de Données (BDD)

- **RGPD et données** : 
En tenant compte de la réglementation RGPD, le stockage de données se fera uniquement sur les nécessaires et les données sensibles qui resteront anonymes.

### 3.2 Politique de mots de passe
- **Utilisation du Hashage** : 
Les mots de passes stockés seront sous forme de hashage permettant ainsi de renforcer la sécurité.
- **Complexité des mots de passe** : 
L'exigeance des mots de passe robustes sera demandée (longueur minimale, caractères spéciaux, chiffres).

### 3.3 UUID
- **Utilisation de UUID** : 
Identification de manière unique, les ressources et les utilisateurs dans la base de données.

### 3.4 Sauvegarde
- **Automatisation des sauvegardes** : 
Mettre en place un système de sauvegarde automatique quotidien.
  - **Heure et fréquence** : 
  Planification des sauvegardes à des heures creuses pour réduire l'impact sur les performances.
- **Politique de rétention** : 
Conserver un nombre défini de sauvegardes sur des supports sécurisés.

## 4. API

### 4.1 Sécurisation des API
- **Utilisation de TLS** : 
Protocole pour sécuriser les données en transit via un système de chiffrement.
- **Utilisation de HSTS** : 
Mettre en œuvre HSTS pour forcer l'utilisation de HTTPS.
- **Utilisation de CORS** : 
Configurer CORS pour contrôler les accès aux ressources.

### 4.2 ORM
- **Utilisation d'un ORM** : 
Utiliser un ORM pour interagir avec la base de données en réduisant les risques SQLi avec à des requêtes préparées.

### 4.3 Authentification
- **Tokens d'authentification** : 
Utiliser des JWT pour gérer les sessions et sécuriser l'authentification des utilisateurs.
- **Limitation des appels API** : 
Limiter le nombre d'appels API pour prévenir des abus et des attaques DDoS.
- **Limitation de tentatives de mots de passe** : 
Bloquer l'accès après un nombre défini de tentatives abusives de connexion.

## 5. Front-End

### Introduction : 
#### Ne pas faire confiance au données envoyées par le client mais implémenter une validation côté serveur.

### 5.1 Protocole de sécurité
- **Utilisation de HTTPS** : 
Garantir que toute la plateforme utilise HTTPS pour sécuriser les données échangées.
  - **Utilisation de TLS** : 
  Configurer TLS pour le chiffrement des communications.
  - **Utilisation de HSTS** : 
  Empêche les utilisateurs d’accéder au site via HTTP non sécurisé et forcer l'utilisation de HTTPS
  
### 5.2 SOP et CORS
- **Utilisation de SOP** : 
Mécanisme de sécurité inclu dans le navigateur pour protéger contre les attaques comme XSS et CSRF.
- **Utilisation de CORS** : 
Contournement de la SOP et restriction des échanges de données entre l'application et le serveur via des en-têtes HTTP.

### 5.3 CSP
- **SRI** : 
Assurer que les ressources externes soient intacts en non comprisent.