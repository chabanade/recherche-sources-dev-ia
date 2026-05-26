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
5. **Inclus la date de consultation `YYYY-MM-DD` pour CHAQUE source** (= aujourd'hui, OBLIGATOIRE depuis V0.2.0).
6. Si tu cites une source qui n'est PAS dans le fichier reference charge, prefixe-la avec **`[HORS-SKILL, à vérifier]`** et invite Mehdi a recroiser avant citation finale.
7. Termine par un piege a eviter pour le sujet en question (issue du skill).

## Format de sortie attendu (V0.2.0, date obligatoire)

```markdown
### Categorie : <nom>
### Date de consultation : YYYY-MM-DD (= aujourd'hui)

**Source 1 — <nom site>**
URL : <url canonique>
Requete pre-remplie : `<requete copy-paste>`
Confiance par defaut : XX%
Consulté le : YYYY-MM-DD

**Source 2 — <nom site>**
[idem avec date]

**Source 3 — <nom site>** [HORS-SKILL, à vérifier]  ← uniquement si la source n'est pas dans le skill
URL : <url canonique a confirmer>
Avertissement : non documentee dans references/*.md du skill, plausible mais a recroiser sur arXiv / site officiel avant citation
Confiance par defaut : non documentee (estimation perso : XX%, a confirmer)
Consulté le : YYYY-MM-DD

### Piege a eviter
<une phrase issue du skill, adaptee au sujet>
```

INTERDIT : inventer un site qui n'est pas dans le skill et le citer comme s'il y etait.
A LA PLACE : si la source est pertinente mais hors-skill, la flagger `[HORS-SKILL, à vérifier]` et proposer a Mehdi de l'ajouter en V0.3.0.

INTERDIT : sortir des URL sans templates de requete.
A LA PLACE : toujours pre-remplir la requete avec les mots-cles fournis en argument.

INTERDIT (V0.2.0) : sortir une URL sans date de consultation.
A LA PLACE : inclure systematiquement `Consulté le : YYYY-MM-DD` sous chaque source. La traçabilite web sans date est inutilisable a 3 mois (sites qui changent, deprecations silencieuses).
