# NexaLab — Document d'Architecture

**Projet Intégrateur · Bloc 2 · Modules 3 & 4**  
Académie de Programmation IFRI · L1 Informatique · Groupe 1 · Mai 2026

---

## Présentation du projet

NexaLab est un laboratoire fictif d'innovation technologique pour les entreprises africaines. Ce dépôt contient la page d'accueil complète conçue et développée par le Groupe 1 dans le cadre du Projet Intégrateur du Bloc 2.

**Contraintes techniques respectées :** HTML & CSS uniquement · Architecture modulaire · HTML5 sémantique · Responsive design · Flexbox · Aucun JavaScript · Aucun framework.

---

## Structure du dépôt

```
nexalab/
│
├── index.html                ← Page d'accueil (9 sections obligatoires)
│
├── styles/
│   ├── base.css              ← Reset + variables CSS + typographie globale
│   ├── header.css            ← Navigation principale (.header, .nav)
│   ├── hero.css              ← Section d'accroche (.hero)
│   ├── about.css             ← Section À propos (.about)
│   ├── services.css          ← Section Services (.services, .service-card)
│   ├── stats.css             ← Chiffres clés (.stats, .stat-card)
│   ├── team.css              ← Section Équipe (.team, .team-card)
│   ├── testimonials.css      ← Témoignages (.testimonials, .testimonial-card)
│   ├── contact.css           ← Formulaire de contact (.contact, .form-group)
│   └── footer.css            ← Pied de page (.footer)
│
└── assets/
    ├── images/               ← Images libres de droits (Unsplash / Pexels)
    └── icons/                ← Icônes SVG
```

---

## Tableau des responsabilités CSS

| Fichier | Responsabilité | Éléments gérés |
|---|---|---|
| `base.css` | Socle commun à toute la page | Reset `*`, variables `:root`, `body`, `img`, `a`, `ul` |
| `header.css` | Barre de navigation | `.header`, `.nav`, `.nav__logo`, `.nav__links`, `.nav__cta`, `.nav__burger` |
| `hero.css` | Section d'accroche principale | `.hero`, `.hero__content`, `.hero__title`, `.hero__subtitle`, `.hero__cta`, `.hero__visual` |
| `about.css` | Section À propos / Mission | `.about`, `.about__content`, `.about__text`, `.about__visual`, `.about__title`, `.about__description` |
| `services.css` | Section Services / Expertises | `.services`, `.services__header`, `.services__grid`, `.service-card`, `.service-card__icon`, `.service-card__title`, `.service-card__description` |
| `stats.css` | Section Chiffres clés | `.stats`, `.stats__grid`, `.stat-card`, `.stat-card__number`, `.stat-card__label` |
| `team.css` | Section Équipe | `.team`, `.team__header`, `.team__grid`, `.team-card`, `.team-card__avatar`, `.team-card__name`, `.team-card__role` |
| `testimonials.css` | Section Témoignages | `.testimonials`, `.testimonials__header`, `.testimonials__grid`, `.testimonial-card`, `.testimonial-card__quote`, `.testimonial-card__author` |
| `contact.css` | Formulaire de contact | `.contact`, `.contact__content`, `.contact__form`, `.form-group`, `input`, `textarea`, `.contact__submit` |
| `footer.css` | Pied de page | `.footer`, `.footer__top`, `.footer__brand`, `.footer__nav`, `.footer__social`, `.footer__contact`, `.footer__bottom` |

---

## Ordre de chargement dans `index.html`

L'ordre des `<link>` est intentionnel : `base.css` est chargé en premier car il définit les variables CSS utilisées par tous les autres fichiers.

```html
<link rel="stylesheet" href="styles/base.css">
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

## Identité visuelle

| Élément | Valeur | Justification |
|---|---|---|
| Fond principal | `#0a0a14` | Sombre profond — identité tech, sérieux |
| Surface carte | `#12122a` / `#1a1a35` | Profondeur visuelle sans contraste brutal |
| Accent principal | `#6c63ff` | Violet électrique — modernité, innovation |
| Accent secondaire | `#00d4aa` | Turquoise — dynamisme, Afrique contemporaine |
| Texte principal | `#e8e8f0` | Blanc cassé — lecture confortable sur fond sombre |
| Texte secondaire | `#8888aa` | Gris bleuté — hiérarchie visuelle claire |

**Typographie :** `Segoe UI` / `system-ui` — natif, performant, lisible à toutes les tailles.

---

## Convention de nommage BEM

Toutes les classes suivent la convention **BEM** (Block__Element--Modifier) :

```
.section          ← Bloc
.section__title   ← Élément du bloc
.section__title--large  ← Modificateur (si variation)
```

Exemples concrets dans ce projet :
- `.nav__logo`, `.nav__links`, `.nav__cta`
- `.service-card__icon`, `.service-card__title`
- `.testimonial-card__quote`, `.testimonial-card__author`

---

## Extensibilité — Ajouter une nouvelle page

Pour ajouter une page (ex: `portfolio.html`) :

1. Créer `nexalab/portfolio.html`
2. Lier `base.css`, `header.css`, `footer.css` (communs à toutes les pages)
3. Créer `styles/portfolio.css` pour les styles spécifiques à cette page uniquement
4. Ne jamais modifier les fichiers existants pour les besoins d'une seule page

```html
<!-- portfolio.html — liens CSS -->
<link rel="stylesheet" href="styles/base.css">
<link rel="stylesheet" href="styles/header.css">
<link rel="stylesheet" href="styles/footer.css">
<link rel="stylesheet" href="styles/portfolio.css">
```

**Règle :** ce qui est commun à plusieurs pages reste dans `styles/`. Ce qui est spécifique à une page va dans son propre fichier.

---

## Branches du dépôt

| Branche | Contenu |
|---|---|
| `main` | Code original du stagiaire — Module 1 (non modifié) |
| `module2` | Architecture modulaire DevStart — Module 2 |
| `projet-integrateur` | Site NexaLab complet — Modules 3 & 4 |

---

## Groupe 1

Académie de Programmation IFRI · L1 Informatique · Mai 2026
