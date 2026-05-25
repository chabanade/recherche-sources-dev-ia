---
description: Ouvre le skill recherche-sources-dev-ia et propose des URL + templates de requete selon le besoin (dev/IA generique, cohorte workshop-01).
argument-hint: [mot-cle ou sujet a chercher — optionnel]
---

Tu es invoque via la commande slash `/recherche-sources`. Charge le skill `recherche-sources-dev-ia` (du plugin mehdi-skills-plugin) et procede comme suit.

**Arguments fournis** : $ARGUMENTS

## Si aucun argument

Presente brievement les 5 categories de sources couvertes par le skill, et demande a Mehdi vers quelle categorie il veut aller :

1. Code & repos (GitHub, Sourcegraph, GitLab, Codeberg)
2. Communaute dev/IA (Reddit, HN, Lobsters, Stack Overflow)
3. Forums officiels (OpenAI, Anthropic, HuggingFace, LangChain Discord)
4. Recherche academique & modeles (arXiv, Papers with Code, HuggingFace, Ollama)
5. Veille / tendances (blogs editeurs, newsletters, podcasts)

## Si arguments fournis

1. Identifie la ou les categories pertinentes parmi les 5 (selon les mots-cles fournis).
2. Charge la reference correspondante (`references/sources-*.md` du skill) pour avoir les templates de requete a jour.
3. Sors 3 a 5 URL canoniques + pour chacune un template de requete pre-rempli avec les arguments de Mehdi.
4. Indique le niveau de confiance par defaut pour chaque source citee.
5. Termine par un piege a eviter pour le sujet en question (issue du skill).

## Format de sortie attendu

```markdown
### Categorie : <nom>

**Source 1 — <nom site>**
URL : <url canonique>
Requete pre-remplie : `<requete copy-paste>`
Confiance par defaut : XX%

**Source 2 — <nom site>**
[idem]

[...]

### Piege a eviter
<une phrase issue du skill, adaptee au sujet>
```

INTERDIT : inventer un site qui n'est pas dans le skill.
A LA PLACE : si la categorie ne couvre pas le besoin, le dire explicitement et proposer a Mehdi d'ajouter la source au skill (version 0.2.0).

INTERDIT : sortir des URL sans templates de requete.
A LA PLACE : toujours pre-remplir la requete avec les mots-cles fournis en argument.
