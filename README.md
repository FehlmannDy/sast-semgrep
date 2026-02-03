# SAST avec Semgrep - Workflow Réutilisable

Ce projet fournit un workflow GitHub Actions réutilisable pour l'analyse statique de code (SAST) utilisant Semgrep.

## 📋 Prérequis

- Un compte [Semgrep Cloud](https://semgrep.dev/)
- Un repository GitHub
- Un token d'API Semgrep

## 🚀 Utilisation

### 1. Configuration du token Semgrep

1. Connectez-vous à [Semgrep Cloud](https://semgrep.dev/)
2. Allez dans **Settings** → **Tokens**
3. Créez un nouveau token d'API
4. Dans votre repository GitHub :
   - Allez dans **Settings** → **Secrets and variables** → **Actions**
   - Cliquez sur **New repository secret**
   - Nom : `SEMGREP_APP_TOKEN`
   - Valeur : votre token Semgrep

### 2. Intégration dans votre projet

Créez un fichier `.github/workflows/sast.yml` dans votre repository avec le contenu suivant :

```yaml
name: My sast pro rules with token
on: [push]
jobs:
  call-sast:
    uses: FehlmannDy/sast-semgrep/.github/workflows/sast-semgrep.yml@main
    secrets:
      SEMGREP_APP_TOKEN: ${{ secrets.SEMGREP_APP_TOKEN }}
```

### 3. Déclenchement automatique

Le workflow se lance automatiquement :
- À chaque push sur la branche `main`
- Lors des pull requests (optionnel, modifiez le trigger `on`)

## 🔧 Fonctionnalités

- ✅ Analyse SAST automatisée avec Semgrep
- ✅ Intégration GitHub Actions
- ✅ Workflow réutilisable
- ✅ Support des règles Semgrep Cloud
- ✅ Rapports de sécurité intégrés

## 📊 Résultats

Les résultats de l'analyse apparaissent dans :
- L'onglet **Security** de votre repository GitHub
- Les logs du workflow dans **Actions**
- Les commentaires sur les pull requests (si configuré)

## ⚙️ Configuration avancée

Pour personnaliser le workflow, vous pouvez :

1. **Modifier les déclencheurs** :
```yaml
on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]
```

2. **Ajouter des conditions** :
```yaml
jobs:
  call-sast:
    if: github.actor != 'dependabot[bot]'
    uses: FehlmannDy/sast-semgrep/.github/workflows/sast-semgrep.yml@main
```

## 🔗 Ressources

- [Documentation Semgrep](https://semgrep.dev/docs/)
- [GitHub Actions](https://docs.github.com/en/actions)
- [Workflow réutilisable](https://docs.github.com/en/actions/using-workflows/reusing-workflows)

## 📝 Support

Pour toute question ou problème, ouvrez une issue dans ce repository.
