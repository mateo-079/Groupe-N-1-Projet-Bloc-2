# NexaLab — Document d'Architecture

**Projet Intégrateur · Bloc 2 · Modules 3 & 4**  
Académie de Programmation IFRI · L1 Informatique · Groupe 1 · Mai 2026

---

## 1. Présentation du projet et du client

**NexaLab** est un laboratoire d'innovation technologique spécialisé dans les solutions numériques pour les entreprises africaines. Leur ADN : modernité, rigueur, impact.

Ce dépôt contient la page d'accueil complète de NexaLab, conçue et développée par le Groupe 1 dans le cadre du Projet Intégrateur du Bloc 2. Le site a été construit de zéro, sans framework ni template, en respectant l'ensemble des contraintes techniques du cahier des charges.

**Audience cible :** directeurs d'entreprise, investisseurs, jeunes talents tech.  
**Objectif :** convaincre en moins de 10 secondes que NexaLab est le bon partenaire technologique.

---

## 2. Structure du dépôt

```
nexalab/
│
├── index.html                        ← Page d'accueil (9 sections obligatoires)
│
├── styles/
│   ├── base.css                      ← Reset universel, variables CSS, typographie
│   │
│   ├── components/                   ← Éléments réutilisables sur plusieurs sections
│   │   ├── buttons.css               ← Tous les boutons (.btn, .btn--gradient, .btn--solid)
│   │   └── cards.css                 ← Squelette structurel des cartes (.card)
│   │
│   ├── header.css                    ← Navigation pill fixe
│   ├── hero.css                      ← Section d'accroche plein écran
│   ├── about.css                     ← Section À propos / Mission
│   ├── services.css                  ← Section Services / Expertises
│   ├── stats.css                     ← Section Chiffres clés
│   ├── team.css                      ← Section Équipe
│   ├── testimonials.css              ← Section Témoignages
│   ├── contact.css                   ← Formulaire de contact
│   └── footer.css                    ← Pied de page
│
└── assets/
    ├── images/                       ← Images libres de droits (Unsplash / Pexels)
    └── icons/                        ← Icônes PNG (réseaux sociaux)
```

### Justification de l'organisation

Le CSS est découpé selon la **règle d'une responsabilité par fichier** : si l'explication de ce que fait un fichier contient le mot « et », c'est qu'il fait trop de choses.

Le dossier `components/` regroupe les seuls éléments qui apparaissent dans plusieurs sections différentes — les boutons (header, hero, footer, contact) et les cartes (services, stats, team, testimonials). Chaque fichier de section surcharge uniquement ce qui lui est propre.

---

## 3. Tableau des responsabilités CSS

| Fichier | Responsabilité | Éléments gérés |
|---|---|---|
| `base.css` | Socle commun à toute la page | Reset `*`, variables `:root`, `body`, `img`, `a`, `ul`, `button`, `.container` |
| `components/buttons.css` | Tous les boutons du site | `.btn`, `.btn--gradient`, `.btn--solid`, `.btn--sm`, `.btn--md`, `.btn--lg` |
| `components/cards.css` | Squelette structurel des cartes | `.card` — border, border-radius, padding, background, hover transform |
| `header.css` | Navigation pill fixe | `.header`, `.nav`, `.nav__logo`, `.nav__links`, `.nav__cta`, `.nav__burger` |
| `hero.css` | Section d'accroche plein écran | `.hero`, `.hero__content`, `.hero__title`, `.hero__subtitle`, `.hero__cta`, `.hero__visual` |
| `about.css` | Section À propos / Mission | `.about`, `.about__content`, `.about__text`, `.about__title`, `.about__description`, `.about__visual` |
| `services.css` | Section Services / Expertises | `.services`, `.services__header`, `.services__grid`, `.service-card` et ses enfants |
| `stats.css` | Section Chiffres clés | `.stats`, `.stats__grid`, `.stat-card`, `.stat-card__number`, `.stat-card__label` |
| `team.css` | Section Équipe | `.team`, `.team__header`, `.team__grid`, `.team-card`, `.team-card__avatar`, `.team-card__name`, `.team-card__role` |
| `testimonials.css` | Section Témoignages | `.testimonials`, `.testimonials__grid`, `.testimonial-card`, `.testimonial-card__quote`, `.testimonial-card__author` |
| `contact.css` | Formulaire de contact | `.contact`, `.contact__content`, `.contact__form`, `.form-group`, `input`, `textarea`, `.contact__submit` |
| `footer.css` | Pied de page | `.footer`, `.footer__body`, `.footer__cta`, `.footer__cols`, `.footer__brand`, `.footer__nav`, `.footer__social`, `.footer__contact`, `.footer__bottom` |

### Ordre de chargement dans `index.html`

L'ordre des `<link>` est critique. Le navigateur lit le CSS de haut en bas.

```html
<!-- 1. Socle global — doit être premier, définit les variables utilisées partout -->
<link rel="stylesheet" href="styles/base.css">

<!-- 2. Composants — doivent être avant les sections qui les surchargent -->
<link rel="stylesheet" href="styles/components/buttons.css">
<link rel="stylesheet" href="styles/components/cards.css">

<!-- 3. Sections — dans l'ordre d'apparition dans la page -->
<link rel="stylesheet" href="styles/header.css">
<link rel="stylesheet" href="styles/hero.css">
<link rel="stylesheet" href="styles/about.css">
<link rel="stylesheet" href="styles/services.css">
<link rel="stylesheet" href="styles/stats.css">
<link rel="stylesheet" href="styles/team.css">
<link rel="stylesheet" href="styles/testimonials.css">
<link rel="stylesheet" href="styles/contact.css">
<link rel="stylesheet" href="styles/footer.css">
```

---

## 4. Choix de design

### Palette de couleurs

| Variable | Valeur | Rôle | Justification |
|---|---|---|---|
| `--color-bg` | `#0a0a14` | Fond principal | Noir bleuté profond — identité tech, sérieux |
| `--color-surface` | `#12122a` | Fond des sections alternées | Légère profondeur sans contraste brutal |
| `--color-surface-2` | `#1a1a35` | Fond des cartes | Troisième niveau de profondeur |
| `--color-accent` | `#6c63ff` | Couleur d'accent principale | Violet électrique — innovation, créativité, tech |
| `--color-accent-2` | `#00d4aa` | Couleur d'accent secondaire | Turquoise — dynamisme, Afrique contemporaine |
| `--color-text` | `#e8e8f0` | Texte principal | Blanc cassé — lecture confortable sur fond sombre |
| `--color-text-muted` | `#8888aa` | Texte secondaire | Hiérarchie visuelle claire |
| `--color-border` | `#2a2a4a` | Bordures | Subtil, ne distrait pas du contenu |

Le contraste violet/turquoise a été choisi pour son caractère à la fois **technologique** (froid, précis) et **africain** (dynamique, vivant). Les deux couleurs ensemble sur fond sombre créent une identité visuelle forte et mémorable.

### Typographie

**Police :** `Segoe UI` / `system-ui` — native au système d'exploitation, aucun chargement externe requis, lisible à toutes les tailles. Ce choix garantit des performances optimales.

**Échelle typographique définie en variables :**

| Variable | Valeur | Usage |
|---|---|---|
| `--font-size-xs` | `0.75rem` | Labels, copyright, uppercase |
| `--font-size-sm` | `0.875rem` | Descriptions, liens nav |
| `--font-size-md` | `1rem` | Texte courant |
| `--font-size-lg` | `1.25rem` | Sous-titres, accroches |
| `--font-size-xl` | `1.5rem` | Titres de cartes |
| `--font-size-2xl` | `2rem` | Titres de sections |
| `--font-size-3xl` | `2.75rem` | Titre contact |
| `--font-size-4xl` | `3.5rem` | Chiffres clés |

### Convention de nommage — BEM

Toutes les classes suivent la convention **BEM** (Block\_\_Element--Modifier) :

```
.section              ← Bloc
.section__element     ← Élément du bloc
.section__element--modifier  ← Variante de l'élément
```

Exemples dans le projet :
- `.nav__logo`, `.nav__links`, `.nav__cta`
- `.service-card__icon`, `.service-card__title`, `.service-card__description`
- `.btn--gradient`, `.btn--solid`, `.btn--lg`

Toutes les classes sont en **anglais**, logiques et descriptives — conformément aux contraintes du cahier des charges.

### Décisions visuelles clés

**Navigation pill fixe** — Le header flotte en haut de page sous forme de pill avec effet glassmorphism (`backdrop-filter: blur`). Ce choix place la navigation au premier plan sans bloquer le contenu. Elle anime son entrée depuis le haut au chargement.

**Visuel hero en CSS pur** — Le visuel de la section hero (orbe lumineux + anneau orbital) est entièrement réalisé en CSS sans image ni SVG externe. Cela démontre la maîtrise des pseudo-éléments et des animations CSS.

**Bordure animée sur les témoignages** — Chaque carte témoignage a une bordure en rotation permanente via `::before` et `::after`. C'est un effet différenciateur qui attire l'œil sur cette section.

**Flexbox comme structure principale** — Tous les layouts (nav, hero, grilles, footer) utilisent Flexbox. CSS Grid est utilisé uniquement pour les stats (grille à 4 colonnes fixes), conformément à la contrainte du CdC.

### Responsive design

| Breakpoint | Cible | Adaptations principales |
|---|---|---|
| `> 1024px` | Desktop | Layout complet, toutes les colonnes visibles |
| `≤ 1024px` | Tablette | Réduction des gaps, ajustement des tailles |
| `≤ 768px` | Mobile | Flex-direction column, navigation burger, cartes pleine largeur |
| `≤ 480px` | Petit mobile | Grille stats 2 colonnes, cartes équipe 1 colonne |

---

## 5. Extensibilité — Ajouter une nouvelle page

L'architecture est conçue pour accueillir de nouvelles pages sans modifier aucun fichier existant.

**Procédure pour ajouter `portfolio.html` :**

1. Créer `nexalab/portfolio.html`
2. Lier uniquement les fichiers partagés + un fichier spécifique

```html
<!-- portfolio.html -->
<link rel="stylesheet" href="styles/base.css">
<link rel="stylesheet" href="styles/components/buttons.css">
<link rel="stylesheet" href="styles/components/cards.css">
<link rel="stylesheet" href="styles/header.css">
<link rel="stylesheet" href="styles/footer.css">
<link rel="stylesheet" href="styles/portfolio.css">  ← nouveau fichier uniquement
```

3. Créer `styles/portfolio.css` pour les styles spécifiques à cette page

**Règle fondamentale :** tout ce qui est commun à plusieurs pages reste dans `styles/`. Tout ce qui est spécifique à une page va dans son propre fichier.

| Page future | Fichiers partagés réutilisés | Fichier spécifique à créer |
|---|---|---|
| `portfolio.html` | base, components, header, footer | `styles/portfolio.css` |
| `blog.html` | base, components, header, footer | `styles/blog.css` |
| `espace-client.html` | base, components, header, footer | `styles/espaceclient.css` |

**Ajouter une nouvelle section à `index.html` :**

1. Créer le bloc HTML dans `index.html` avec les classes BEM appropriées
2. Créer `styles/nouvellesection.css` avec les styles de cette section
3. Ajouter le `<link>` correspondant dans `index.html`
4. Ne modifier aucun autre fichier CSS existant

---

## 6. Sections de la page

| # | Section | Balise HTML | Fichier CSS |
|---|---|---|---|
| 01 | Header & Navigation | `<header>` | `header.css` |
| 02 | Hero | `<section>` | `hero.css` |
| 03 | À propos / Mission | `<section>` | `about.css` |
| 04 | Services / Expertises | `<section>` | `services.css` |
| 05 | Chiffres clés | `<section>` | `stats.css` |
| 06 | Équipe | `<section>` | `team.css` |
| 07 | Témoignages | `<section>` | `testimonials.css` |
| 08 | Formulaire de contact | `<section>` | `contact.css` |
| 09 | Footer | `<footer>` | `footer.css` |

---

## 7. Branches du dépôt

| Branche | Contenu |
|---|---|
| `main` | Code original du stagiaire — Module 1 (non modifié, référence) |
| `module2` | Architecture modulaire DevStart — Module 2 |
| `projet-integrateur` | Site NexaLab complet — Projet Intégrateur |
| `test` | Site NexaLab complet — Branche de test |

---



*Académie de Programmation IFRI · L1 Informatique · Bloc 2 · Mai 2026*