# Les Gets Trails

Projet d'apprentissage CSS
Mise en pratique des bonnes pratiques CSS modernes autour d'un site de randonnées à Les Gets (Haute-Savoie).

## Structure du projet

```
lesgets-hiking/
├── index.html
├── css/
│   ├── main.css                      ← point d'entrée, ordre des @layer
│   ├── tokens/
│   │   └── design-tokens.css         ← variables CSS (design system)
│   ├── layers/
│   │   ├── reset.css                 ← reset navigateur moderne
│   │   ├── base.css                  ← styles éléments HTML + .btn
│   │   ├── layout.css                ← structures de mise en page
│   │   └── utilitaires.css           ← classes atomiques
│   └── composants/
│       ├── nav.css                   ← navigation principale
│       ├── hero.css                  ← section hero
├── assets/
│   └── images/
└── README.md
```

## Variables

### Primitives

Les valeurs brutes de la palette : couleurs concrètes (`--vert-500`, `--sable-100`), tailles de texte, rayons… Elles ne disent pas _à quoi_ elles servent, juste _ce qu'elles sont_.

### Sémantiques

Des alias qui donnent un sens fonctionnel aux primitives :

```css
--color-bg: var(--grey-50); /* "fond de page" → pointe vers une primitive */
--color-primary: var(--vert-500); /* "couleur principale" */
```

L'intérêt : si tu changes de thème ou de palette, tu ne touches qu'aux sémantiques (ou au dark mode override), pas à chaque composant. Les composants n'utilisent jamais `--vert-500` directement, seulement `--color-primary`.
