# Les Gets Trails

Projet d'apprentissage CSS — mise en pratique des bonnes pratiques CSS modernes autour d'un site de randonnées à Les Gets (Haute-Savoie).

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
