# Fiche Grèce — août 2026

Page unique installable sur téléphone. Programme, hôtels, transports et repères pratiques. Fonctionne hors ligne une fois ouverte.

## Ce qui n'est pas dans ce dépôt

Volontairement absents, parce que le dépôt est public :

- numéros de confirmation d'hôtel
- références de vol et de ferry
- noms des voyageurs, numéros de téléphone personnels, moyens de paiement
- montants payés

Ne pas les rajouter. Les confirmations restent dans la boîte mail. Les numéros de téléphone présents sont ceux des hôtels, qui sont publics.

## Mise en ligne

```bash
git init
git add .
git commit -m "Fiche voyage Grèce 2026"
gh repo create grece-2026 --public --source=. --push
```

Puis **Settings → Pages → Deploy from a branch → main / (root) → Save**.

L'adresse sera `https://<utilisateur>.github.io/grece-2026/` après une minute ou deux.

Sans la CLI `gh` : créer le dépôt sur github.com, puis

```bash
git remote add origin https://github.com/<utilisateur>/grece-2026.git
git branch -M main
git push -u origin main
```

## Installation sur le téléphone

**iPhone** — ouvrir l'adresse dans Safari (l'installation ne marche que depuis Safari), bouton Partager, *Sur l'écran d'accueil*.

**Android** — Chrome, menu ⋮, *Installer l'application*.

Icône sur l'écran d'accueil, lancement plein écran, fonctionnement hors ligne complet.

## Modifier

Tout est dans `index.html`. Après une modification :

```bash
git add . && git commit -m "maj" && git push
```

Incrémenter `const CACHE = 'grece-2026-v1'` dans `sw.js` (`v2`, `v3`…), sinon le téléphone continue de servir l'ancienne version depuis son cache.

## Structure

| Fichier | Rôle |
|---|---|
| `index.html` | toute la fiche, contenu et style compris |
| `manifest.webmanifest` | nom, icônes, mode plein écran |
| `sw.js` | cache hors ligne |
| `icon-*.png` | icônes d'application |

## À vérifier avant de partir

Les informations pratiques de l'onglet Repères ont été rassemblées le 13 août 2026. Trois points bougent :

- le tarif de l'Acropole (sources divergentes entre 20 et 30 €) — vérifier sur hhticket.gr
- la porte du ferry au Pirée — vérifier sur le billet et les panneaux du port
- les fermetures de sites pour cause de canicule — décidées au jour le jour
