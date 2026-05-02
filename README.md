# DevStart Agency — Site Web

**Bloc 2 · Module 2 — Architecture logicielle & modularité**  
Académie de Programmation IFRI · L1 Informatique · Groupe 1 · Avril 2026

---

## 📌 À propos de ce dépôt

Ce dépôt contient le site vitrine de **DevStart Agency**, une agence web fictive utilisée comme support pédagogique dans le cadre du Bloc 2 · Module 2 de l'Académie de Programmation IFRI.

### Branches

| Branche | Contenu |
|---|---|
| `main` | Code original du Module 1 — tel que livré par le stagiaire (non modifié) |
| `module2` | Code réorganisé selon l'architecture modulaire conçue par le Groupe 1 |

> ⚠️ La branche `main` ne doit pas être modifiée. Elle sert de référence pour comparer l'avant et l'après.

---

## 🗂️ Structure du projet (branche `module2`)

```
devstart/
│
├── index.html                  ← Page d'accueil (inchangée visuellement)
│
├── styles/
│   ├── base.css                ← Reset universel + styles globaux (*, body)
│   ├── header.css              ← Barre de navigation (.b1, .b1a, .b1b)
│   ├── hero.css                ← Section d'accueil (.c, .c1, .c2...)
│   ├── services.css            ← Section services (.d, .dd, cartes)
│   ├── about.css               ← Section À propos (.e, .e1, .e2...)
│   ├── testimonials.css        ← Section témoignages (.f, .ff, cartes)
│   ├── contact.css             ← Formulaire de contact (.g, .gi, .gt, .gb)
│   ├── footer.css              ← Pied de page (.h, .h1, .h2, .h3)
│   │
│   └── components/
│       ├── buttons.css         ← Tous les boutons du site (.btn, .btn-primary, .btn-dark)
│       └── cards.css           ← Squelette structurel commun des cartes (.card)
│
├── pages/                      ← Futures pages prévues (non encore développées)
│   ├── portfolio.html
│   ├── blog.html
│   └── espace-client.html
│
└── assets/
    └── images/
        ├── hero.png
        └── team.png
```

---

## 🧩 Principe d'architecture

Ce module applique la **règle d'une responsabilité par fichier** :

> _Si tu dois expliquer ce que fait un fichier et que ta réponse contient le mot « et », c'est qu'il fait trop de choses._

**Avant (Module 1)** — un seul `style.css` de ~200 lignes gérait simultanément la navigation, le hero, les cartes, les témoignages, le formulaire et le footer.

**Après (Module 2)** — 10 fichiers CSS, chacun avec une seule responsabilité claire.

---

## 📂 Ordre de chargement des CSS dans `index.html`

L'ordre des balises `<link>` est critique. Le navigateur lit le CSS de haut en bas — `base.css` et les composants doivent être déclarés avant les fichiers de section.

```html
<!-- 1. Socle global -->
<link rel="stylesheet" href="styles/base.css">

<!-- 2. Composants réutilisables -->
<link rel="stylesheet" href="styles/components/buttons.css">
<link rel="stylesheet" href="styles/components/cards.css">

<!-- 3. Sections de la page -->
<link rel="stylesheet" href="styles/header.css">
<link rel="stylesheet" href="styles/hero.css">
<link rel="stylesheet" href="styles/services.css">
<link rel="stylesheet" href="styles/about.css">
<link rel="stylesheet" href="styles/testimonials.css">
<link rel="stylesheet" href="styles/contact.css">
<link rel="stylesheet" href="styles/footer.css">
```

---

## ♻️ Composants réutilisables

### `components/buttons.css`

Trois boutons existent dans le code, répartis dans trois sections différentes. Ils partagent la même logique (fond coloré, texte blanc, bold, border-radius). `buttons.css` centralise ce style pour éviter la duplication.

```css
.btn          { color: white; font-weight: bold; padding: 14px 32px; border-radius: 6px; }
.btn-primary  { background: #e94560; }
.btn-dark     { background: #1a1a2e; }
```

### `components/cards.css`

Les cartes Services et Témoignages partagent le même squelette (bloc arrondi, padding). `cards.css` définit la structure ; chaque fichier de section surcharge uniquement la couleur.

```css
/* cards.css — squelette commun */
.card { padding: 28px; border-radius: 10px; }

/* services.css — surcharge couleur */
.service-card { background: #f4f4f4; }

/* testimonials.css — surcharge couleur */
.testimonial-card { background: #16213e; }
```

---

## 🚀 Stratégie d'évolution — Futures pages

Les futures pages (Portfolio, Blog, Espace Client) n'ont pas besoin de réécrire les styles communs. Elles lient simplement les fichiers partagés et ajoutent uniquement leurs styles spécifiques.

| Page | Fichiers partagés réutilisés | Fichier spécifique |
|---|---|---|
| `portfolio.html` | base, header, footer, buttons, cards | `styles/portfolio.css` |
| `blog.html` | base, header, footer, buttons | `styles/blog.css` |
| `espace-client.html` | base, header, footer, buttons | `styles/espaceclient.css` |

**Règle :** tout ce qui est commun à plusieurs pages reste dans `styles/`. Tout ce qui est spécifique à une page va dans un fichier propre à cette page.

---

## ✅ Vérification

La page doit rester **visuellement identique** à celle du Module 1 après la réorganisation. Si quelque chose casse visuellement, c'est une erreur de chemin dans un `<link>` ou une règle CSS oubliée dans le découpage.

Pour vérifier : ouvrir `index.html` dans le navigateur et comparer section par section avec la version `main`.

---

## 👥 Groupe 1

Académie de Programmation IFRI · L1 Informatique · Avril 2026