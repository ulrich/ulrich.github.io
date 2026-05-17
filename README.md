# ulrich.github.io — Notes de maintenance

## Branches

| Branche | Rôle |
|---|---|
| `src` | Sources Hugo (branche de travail uniquement) |
| `master` | Le site généré est déployé automatiquement par GitHub Actions |

**Ne jamais modifier `master` directement.**

## Mettre à jour le site

1. Se placer sur la branche `src`
2. Modifier `src/config.toml` (expériences, compétences, etc.)
3. Pusher :

```bash
git add .
git commit -m "Update CV"
git push origin src
```

GitHub Actions build Hugo et déploie automatiquement sur `master` → [reservoircode.net](https://reservoircode.net).

## Ajouter/modifier une expérience

Dans `src/config.toml`, chaque expérience suit ce format :

```toml
[[params.experience.list]]
title = "Mon titre"
dates = "01/2024 – Present"
company = "Société · Contexte · Lieu"
stack = "Java, Spring Boot, Docker..."
details = """
Description en **Markdown**.

Deuxième paragraphe.
"""
```

## Modifier le template HTML

Les partials surchargés (prioritaires sur le thème) sont dans `src/layouts/partials/`.
Le thème original est dans `src/themes/devresume/layouts/partials/`.

## Mettre à jour le thème

```bash
cd src/themes/devresume
git checkout master
git pull origin master
cd ../../..
git add src/themes/devresume
git commit -m "Update theme"
git push origin src
```

## Points importants

- Le SCSS nécessite **Hugo Extended** (configuré dans le workflow)
- La couleur principale est `primaryColor` dans `[params]` du `config.toml`
- L'avatar est dans `src/static/assets/images/avatar.png`
- Le `CNAME` (`reservoircode.net`) est regénéré automatiquement à chaque déploiement
