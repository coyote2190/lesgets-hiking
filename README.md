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
│       └── carte-rando.css           ← carte de randonnée
├── assets/
│   └── images/
└── README.md
```

## Concepts CSS appliqués

### 1. Cascade Layers (`@layer`)

L'ordre de priorité est déclaré **une seule fois** dans `main.css` :

```css
@layer reset, base, layout, composants, utilitaires;
```

Avantage : peu importe la spécificité d'un sélecteur dans `reset`, il ne pourra jamais écraser un style de `utilitaires`. La cascade est **explicite et prévisible**.

### 2. Design Tokens (variables CSS)

Toutes les valeurs du design system sont centralisées dans `tokens/design-tokens.css` :

- Couleurs (palette + sémantique)
- Typographie fluide avec `clamp()`
- Espacement sur une échelle cohérente
- Ombres, rayons, transitions

### 3. Typographie fluide

```css
--taille-4xl: clamp(2.5rem, 2rem + 2vw, 3.5rem);
```

La taille s'adapte progressivement entre mobile et desktop — sans media query.

### 4. Propriétés logiques

```css
padding-inline: var(--padding-page); /* au lieu de padding-left/right */
inset-block-start: 0; /* au lieu de top: 0 */
max-inline-size: 100%; /* au lieu de max-width */
```

Facilite l'internationalisation (RTL/LTR).

### 5. Variantes via custom properties locales

Dans `carte-rando.css`, le badge de difficulté utilise une variable "privée" :

```css
.carte-rando__badge {
  --_couleur-badge: var(--couleur-neutre-500); /* valeur par défaut */
  background-color: var(--_couleur-badge);
}

.carte-rando__badge--facile {
  --_couleur-badge: var(--couleur-facile);
}
.carte-rando__badge--intermediaire {
  --_couleur-badge: var(--couleur-intermediaire);
}
.carte-rando__badge--difficile {
  --_couleur-badge: var(--couleur-difficile);
}
```

Un seul endroit à maintenir pour toutes les variantes.

### 6. Grille responsive sans media query

```css
grid-template-columns: repeat(auto-fill, minmax(min(300px, 100%), 1fr));
```

`auto-fill` + `minmax` + `min()` : les colonnes s'adaptent automatiquement selon l'espace disponible.

### 7. Reset moderne

Basé sur Andy Bell et Josh Comeau :

- `box-sizing: border-box` universel
- `ul[role="list"]` reseté (sémantique d'abord)
- Respect de `prefers-reduced-motion`
- `focus-visible` accessible

### 8. Accessibilité

- Titres hiérarchisés (`h1` → `h2` → `h3`)
- `aria-label` sur les éléments interactifs
- `role="list"` + `list-style: none` (convention VoiceOver)
- `.sr-only` pour les labels visuellement masqués
- `:focus-visible` pour la navigation clavier

## Lancer le projet

Ouvrir `index.html` directement dans un navigateur, ou utiliser l'extension **Live Server** dans VS Code.

```bash
# Avec npx serve (optionnel)
npx serve .
```

## Références

- [CSS Cascade Layers — MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/@layer)
- [A Modern CSS Reset — Andy Bell](https://piccalil.li/blog/a-more-modern-css-reset/)
- [CSS Custom Reset — Josh Comeau](https://www.joshwcomeau.com/css/custom-css-reset/)
- [Logical Properties — MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_logical_properties_and_values)
- [clamp() — MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/clamp)
