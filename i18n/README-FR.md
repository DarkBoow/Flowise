<!-- markdownlint-disable MD030 -->

<img width="100%" src="https://github.com/FlowiseAI/Flowise/blob/main/images/flowise.png?raw=true"></a>

# Flowise - Créez facilement des applications LLM

[![Release Notes](https://img.shields.io/github/release/FlowiseAI/Flowise)](https://github.com/FlowiseAI/Flowise/releases)
[![Discord](https://img.shields.io/discord/1087698854775881778?label=Discord&logo=discord)](https://discord.gg/jbaHfsRVBW)
[![Twitter Follow](https://img.shields.io/twitter/follow/FlowiseAI?style=social)](https://twitter.com/FlowiseAI)
[![GitHub star chart](https://img.shields.io/github/stars/FlowiseAI/Flowise?style=social)](https://star-history.com/#FlowiseAI/Flowise)
[![GitHub fork](https://img.shields.io/github/forks/FlowiseAI/Flowise?style=social)](https://github.com/FlowiseAI/Flowise/fork)

[English](../README.md) | [中文](./README-ZH.md) | [日本語](./README-JA.md) | [한국어](./README-KR.md) | Français

<h3>Interface glisser‑déposer pour créer votre propre flux LLM</h3>
<a href="https://github.com/FlowiseAI/Flowise">
<img width="100%" src="https://github.com/FlowiseAI/Flowise/blob/main/images/flowise.gif?raw=true"></a>

## ⚡ Démarrage rapide

Installez [NodeJS](https://nodejs.org/en/download) version 18.15.0 ou plus récente.

1. Installation de Flowise
    ```bash
    npm install -g flowise
    ```
2. Lancement de Flowise

    ```bash
    npx flowise start
    ```

    Avec un nom d'utilisateur et un mot de passe

    ```bash
    npx flowise start --FLOWISE_USERNAME=user --FLOWISE_PASSWORD=1234
    ```

3. Ouvrez [http://localhost:3000](http://localhost:3000)

## 🐳 Docker

### Docker Compose

1. Rendez‑vous dans le dossier `docker` à la racine du projet
2. Copiez le fichier `.env.example`, collez‑le au même endroit et renommez‑le en `.env`
3. `docker compose up -d`
4. Ouvrez [http://localhost:3000](http://localhost:3000)
5. Pour arrêter les conteneurs : `docker compose stop`

### Image Docker

1. Construisez l'image localement :
    ```bash
    docker build --no-cache -t flowise .
    ```
2. Exécutez l'image :

    ```bash
    docker run -d --name flowise -p 3000:3000 flowise
    ```

3. Arrêtez l'image :
    ```bash
    docker stop flowise
    ```

## 👨‍💻 Développeurs

Flowise est un mono‑répertoire comprenant trois modules principaux :

- `server` : serveur Node fournissant les API
- `ui` : interface React
- `components` : intégrations tierces sous forme de nœuds
- `api-documentation` : documentation API Swagger générée automatiquement

### Prérequis

- Installer [PNPM](https://pnpm.io/installation)
    ```bash
    npm i -g pnpm
    ```

### Mise en place

1. Clonez le dépôt
    ```bash
    git clone https://github.com/FlowiseAI/Flowise.git
    ```
2. Placez‑vous dans le dossier
    ```bash
    cd Flowise
    ```
3. Installez les dépendances de tous les modules :
    ```bash
    pnpm install
    ```
4. Compilez l'ensemble du code :
    ```bash
    pnpm build
    ```
    <details>
    <summary>Code d’erreur 134 (mémoire insuffisante)</summary>
      Si cette erreur apparaît lors de l’exécution de `pnpm build`, augmentez la taille du tas Node.js puis relancez :

        export NODE_OPTIONS="--max-old-space-size=4096"
        pnpm build

    </details>
5. Démarrez l’application :
    ```bash
    pnpm start
    ```
    L’application est alors accessible sur [http://localhost:3000](http://localhost:3000)
6. Pour un environnement de développement :
    - Créez un fichier `.env` dans `packages/ui` et renseignez `VITE_PORT` (voir `.env.example`)
    - Créez un fichier `.env` dans `packages/server` et renseignez `PORT` (voir `.env.example`)
    - Lancez
        ```bash
        pnpm dev
        ```
    Toute modification rechargera automatiquement l’application sur [http://localhost:8080](http://localhost:8080)

## 🔒 Authentification

Pour activer l’authentification applicative, ajoutez `FLOWISE_USERNAME` et `FLOWISE_PASSWORD` dans le fichier `.env` de `packages/server` :

```
FLOWISE_USERNAME=user
FLOWISE_PASSWORD=1234
```

## 🌱 Variables d’environnement

De nombreuses variables permettent de configurer votre instance. Reportez‑vous au fichier `.env.example` de `packages/server` pour la liste complète. Les principales sont :

- **PORT** : port du serveur (par défaut 3000)
- **DATABASE_PATH** et paramètres associés pour la base de données
- **FLOWISE_USERNAME** / **FLOWISE_PASSWORD** : identifiants d’accès
- **LOG_PATH** et **LOG_LEVEL** pour la journalisation
- **STORAGE_TYPE** et options S3 pour le stockage des fichiers
- **SHOW_COMMUNITY_NODES** pour afficher les nœuds communautaires

## 📖 Documentation

[Documentation Flowise](https://docs.flowiseai.com/)

## 🌐 Auto‑hébergement

Déployez Flowise sur votre infrastructure grâce aux [guides de déploiement](https://docs.flowiseai.com/configuration/deployment) :

- [AWS](https://docs.flowiseai.com/deployment/aws)
- [Azure](https://docs.flowiseai.com/deployment/azure)
- [Digital Ocean](https://docs.flowiseai.com/deployment/digital-ocean)
- [GCP](https://docs.flowiseai.com/deployment/gcp)
- <details>
  <summary>Autres</summary>

  - [Railway](https://docs.flowiseai.com/deployment/railway)
    
    [![Deploy on Railway](https://railway.app/button.svg)](https://railway.app/template/pn4G8S?referralCode=WVNPD9)
  - [Render](https://docs.flowiseai.com/deployment/render)
    
    [![Deploy to Render](https://render.com/images/deploy-to-render-button.svg)](https://docs.flowiseai.com/deployment/render)
  - [HuggingFace Spaces](https://docs.flowiseai.com/deployment/hugging-face)
    
    <a href="https://huggingface.co/spaces/FlowiseAI/Flowise"><img src="https://huggingface.co/datasets/huggingface/badges/raw/main/open-in-hf-spaces-sm.svg" alt="HuggingFace Spaces"></a>
  - [Elestio](https://elest.io/open-source/flowiseai)
    
    [![Deploy on Elestio](https://elest.io/images/logos/deploy-to-elestio-btn.png)](https://elest.io/open-source/flowiseai)
  - [Sealos](https://cloud.sealos.io/?openapp=system-template%3FtemplateName%3Dflowise)
    
    [![](https://raw.githubusercontent.com/labring-actions/templates/main/Deploy-on-Sealos.svg)](https://cloud.sealos.io/?openapp=system-template%3FtemplateName%3Dflowise)
  - [RepoCloud](https://repocloud.io/details/?app_id=29)
    
    [![Deploy on RepoCloud](https://d16t0pc4846x52.cloudfront.net/deploy.png)](https://repocloud.io/details/?app_id=29)
  </details>

## ☁️ Flowise Cloud

[Commencer avec Flowise Cloud](https://flowiseai.com/)

## 🙋 Support

Questions, problèmes ou demandes de fonctionnalités ? Rendez‑vous dans la section [discussion](https://github.com/FlowiseAI/Flowise/discussions).

## 🙌 Contribuer

Merci aux formidables contributeurs

<a href="https://github.com/FlowiseAI/Flowise/graphs/contributors">
<img src="https://contrib.rocks/image?repo=FlowiseAI/Flowise" />
</a>

Consultez le [guide de contribution](CONTRIBUTING.md). Vous pouvez également nous rejoindre sur [Discord](https://discord.gg/jbaHfsRVBW) pour toute question ou problème.
[![Star History Chart](https://api.star-history.com/svg?repos=FlowiseAI/Flowise&type=Timeline)](https://star-history.com/#FlowiseAI/Flowise&Date)

## 📄 Licence

Le code source de ce dépôt est distribué sous [Licence Apache 2.0](LICENSE.md).
