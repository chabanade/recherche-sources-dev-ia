# Sources Code & Repos — Templates de requete

Documentation chargee a la demande par le skill `recherche-sources-dev-ia`.

---

## GitHub Search

URL : https://github.com/search

### Templates copiables

Repo IA recent et actif :
```
language:python topic:rag stars:>100 pushed:>2026-01-01
```

Implementation d'un skill Claude Code :
```
path:.claude/skills lang:markdown stars:>5
```

Exemples de hooks Claude Code :
```
path:.claude/hooks lang:json
```

Workflows GitHub Actions IA :
```
path:.github/workflows "anthropic" OR "openai" lang:yaml stars:>10
```

Code lie a un papier specifique :
```
"arxiv 2502.01234" in:readme
```

Filtres utiles :
- `language:X` (python, typescript, rust, go...)
- `topic:Y` (rag, llm, agents, vector-database, mcp...)
- `stars:>N` (qualite)
- `pushed:>YYYY-MM-DD` (fraicheur)
- `path:chemin` (fichier specifique au repo)
- `in:readme "..."` (recherche dans le README)
- `org:anthropic` ou `user:nomuser` (scope a une orga)

### Piege connu

INTERDIT : prendre un repo "best practices" SEO-engineered (titre flashy, README marketing, peu de commits).
A LA PLACE : verifier l'onglet "Insights → Code frequency" pour voir si le repo vit, et lire 2-3 commits pour juger la qualite reelle.

Confiance par defaut : 75% pour stars > 100 et push < 6 mois. 50% sinon.

---

## GitHub Trending

URL : https://github.com/trending

Filtres : langage + plage (daily / weekly / monthly).

Utile pour reperer ce qui monte cette semaine sans avoir d'idee precise.

### Piege connu

INTERDIT : prendre un repo trending comme reference technique.
A LA PLACE : le considerer comme un signal, puis evaluer comme un repo normal (stars cumules, age, derniere maj).

Pourquoi : le trending est biaise par les pics de viralite (HN, X). Un repo trending peut etre un toy project.

---

## Sourcegraph

URL : https://sourcegraph.com/search

Indexe des dizaines de milliers de repos publics. Permet la recherche **dans le code** plus puissante que GitHub.

### Templates copiables

Recherche d'usage d'une API :
```
repo:^github\.com/anthropic content:"messages.create" lang:python
```

Patterns regex :
```
patterntype:regexp lang:typescript "new\s+Anthropic\("
```

### Piege connu

INTERDIT : confondre Sourcegraph cloud (gratuit, repos publics) avec Sourcegraph self-hosted.
A LA PLACE : utiliser https://sourcegraph.com pour les recherches publiques, c'est suffisant.

---

## GitLab + Codeberg

URL GitLab : https://gitlab.com/search
URL Codeberg : https://codeberg.org/explore/repos

Utiles pour les projets europeens (souverainete) ou hors-GitHub (mouvance free software, projets gouvernementaux).

### Piege connu

INTERDIT : assumer qu'un projet n'existe pas car absent de GitHub.
A LA PLACE : verifier aussi GitLab et Codeberg pour les projets europeens et gov.

Confiance par defaut : 70% (ecosysteme plus petit donc moins de signal social, mais souvent qualite tech equivalente).
