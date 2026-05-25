---
name: recherche-sources-dev-ia
version: "0.1.0"
status: draft
last-updated: "2026-05-26"
changelog: |
  0.1.0 (2026-05-26) - Creation initiale, issue Meydeey workshop-01 du 25/05 14:15. Skill cohorte generique Dev + IA. Skill metier Tesla a venir en v2.
description: >
  This skill should be used when Mehdi or any cohort member searches for dev/AI resources, repos, forum threads, papers, models or trends. Triggers on phrases like "cherche un repo GitHub", "trouve un repo", "thread Reddit sur LLM", "post r/LocalLLaMA", "forum OpenAI", "community OpenAI", "papier arXiv", "Hugging Face model", "leaderboard MTEB", "tendance IA recente", "veille IA", "Stack Overflow tag claude", "exemple LangChain", "benchmark embedding", "trouve une source", "ou je peux chercher". Centralise 30+ sources high-signal avec templates de requete copiables et pieges connus.
---

# Recherche Sources Dev / IA — Listing Cohorte Workshop-01

Skill cohorte : centralise les sources de recherche utiles pour le dev et l'IA, avec **prompts de requete copiables** et **pieges connus** par site. Issue : post Meydeey 25/05 14:15 sur `#workshop-01-base-memorielle`.

INTERDIT : googler "best LLM repo 2026" et copier le premier resultat.
A LA PLACE : passer par le site canonique (GitHub Search, arXiv, HuggingFace leaderboard) avec une requete filtree, puis citer la source.

---

## Avant de chercher

### Choisir la categorie selon le besoin

| Besoin | Categorie cible | Reference detaillee |
|--------|-----------------|---------------------|
| Trouver un repo de code, exemple d'implementation | Code & repos | `references/sources-code-repos.md` |
| Verifier qu'un probleme rencontre par d'autres devs | Communaute dev/IA | `references/sources-communaute.md` |
| Lire la doc/forum officiel d'un editeur (OpenAI, Anthropic, HuggingFace) | Forums officiels | `references/sources-communaute.md` |
| Lire un papier de recherche, benchmark, leaderboard | Recherche & modeles | `references/sources-recherche-ia.md` |
| Suivre une tendance, voir ce qui sort cette semaine | Veille / tendances | `references/sources-veille.md` |
| Question pointue avec snippet de code | Q&A pointu | `references/sources-communaute.md` |

INTERDIT : taper "claude rag" dans Google.
A LA PLACE : decider d'abord la categorie ci-dessus, puis aller sur le site canonique avec une requete filtree.

### Fixer le niveau de confiance attendu

Avant de chercher, decider ce qu'on attend de la source :

| Source | Confiance par defaut | Quand l'utiliser |
|--------|---------------------|------------------|
| Doc officielle editeur (Anthropic, OpenAI, HuggingFace) | 95% | Verite normative |
| Papier arXiv revise, code public, citations > 50 | 85% | Methode/algorithme |
| Repo GitHub stars > 100, last push < 6 mois | 75% | Implementation exemple |
| Reddit/HN post upvote eleve, commentaires riches | 60% | Signal qualitatif |
| Blog/newsletter editeur tiers | 50% | Tendance, a recroiser |
| Post Twitter/X isole | 30% | Indice, jamais source unique |

Reutilise la doctrine `verite-anti-hallucination`. Toute source < 80% doit etre recroisee avant citation.

---

## Pendant la recherche

### Les 5 categories (vue d'ensemble)

#### 1. Code & repos
Sites principaux : GitHub Search, GitHub Trending, Sourcegraph, GitLab, Codeberg.
Voir `references/sources-code-repos.md` pour les templates exacts.

Exemple rapide GitHub :
```
language:python topic:rag stars:>100 pushed:>2026-01-01
```

#### 2. Communaute dev/IA
Sites principaux : Reddit (r/MachineLearning, r/LocalLLaMA, r/LangChain, r/ClaudeAI), HackerNews, Lobsters.
Voir `references/sources-communaute.md`.

Exemple rapide Reddit :
```
site:reddit.com/r/LocalLLaMA "Qwen 3" "fine-tune"
```

#### 3. Forums officiels
Sites principaux : community.openai.com, docs.anthropic.com, discuss.huggingface.co, Discord LangChain.
Voir `references/sources-communaute.md`.

#### 4. Recherche academique & modeles
Sites principaux : arXiv (cs.CL, cs.AI), Papers with Code, OpenReview, Semantic Scholar, Connected Papers, HuggingFace (models + datasets + leaderboards MTEB), Replicate, Ollama library.
Voir `references/sources-recherche-ia.md`.

Exemple rapide arXiv :
```
cat:cs.CL "retrieval augmented" 2026
```

#### 5. Veille / tendances
Sites principaux : Anthropic news, OpenAI blog, LangChain blog, The Batch (deeplearning.ai), AlphaSignal, MarkTechPost, Last Week in AI, Latent Space podcast.
Voir `references/sources-veille.md`.

### Construire une bonne requete

Format standard a respecter :

```
<scope:site/categorie> <mot-cle-principal> <filtre-temps> <filtre-qualite>
```

Exemple :
```
site:github.com path:.claude/skills lang:markdown stars:>10
```

Pourquoi : sans filtres, les resultats sont satures de contenu bas signal (blogs SEO, vieux tutos). Filtrer par date + popularite + scope ramene le ratio signal/bruit a un niveau exploitable.

---

## Apres la recherche

### Citer la source

Format standard a coller dans le doc/commit/message :

```markdown
Source : [Titre court](URL canonique) — site/auteur, date YYYY-MM-DD, confiance XX%.
```

Exemple :
```markdown
Source : [GitHub thedotmack/claude-mem](https://github.com/thedotmack/claude-mem) — release v13.3.0 du 21/05/2026, confiance 75% (repo recent, stars eleves, pas encore teste en interne).
```

INTERDIT : citer "j'ai vu sur Reddit que..." sans URL ni date.
A LA PLACE : copier l'URL exacte du post + date + flair/auteur.

### Verifier avant d'agir

Application du skill `verite-anti-hallucination` :

```
[ ] URL canonique recopiee (pas un raccourci bit.ly)
[ ] Date de la source notee
[ ] Niveau de confiance estime
[ ] Source recroisee si confiance < 80%
[ ] Aucune affirmation factuelle non sourcee
```

### Sauvegarder une trouvaille reutilisable

Si la source merite d'etre retrouvee dans 3 mois, declencher `documentation-7-destinations` pour la ranger au bon endroit (MEMORY.md, AGEA save_memory, brain/, ou dans le projet concerne).

INTERDIT : laisser une URL precieuse dans le scrollback du terminal.
A LA PLACE : la sauvegarder via les 7 destinations.

---

## Pieges a eviter

### Piege 1 : Repo abandonne pris pour vivant

INTERDIT : citer un repo GitHub sans regarder la date du dernier commit.
A LA PLACE : filtrer `pushed:>2026-01-01` sur GitHub Search, ou regarder l'onglet "Insights → Commits" avant de citer.

Pourquoi : l'ecosysteme IA bouge tres vite. Un repo de 2024 est souvent obsolete (mauvais nom de modele, API depreciee).

### Piege 2 : Post Reddit isole pris pour consensus

INTERDIT : tirer une conclusion d'un seul thread Reddit.
A LA PLACE : recroiser avec un papier arXiv ou un repo qui implemente la meme idee.

Pourquoi : un post upvote peut etre populaire pour de mauvaises raisons (humour, drama). Le signal qualitatif n'est utile que recroise.

### Piege 3 : Confondre community.openai.com avec docs officielle

INTERDIT : citer un post du forum community comme s'il etait normatif.
A LA PLACE : prefixer par "post forum community" ou aller chercher la version doc officielle (platform.openai.com/docs).

### Piege 4 : Lire un papier sans regarder s'il a du code

INTERDIT : citer une methode d'un papier arXiv sans verifier qu'elle est implementable.
A LA PLACE : croiser avec Papers with Code (paperswithcode.com) ou chercher le repo des auteurs sur GitHub.

### Piege 5 : Tomber sur du contenu SEO low-quality

INTERDIT : ouvrir un blog "Top 10 best LLM frameworks 2026" qui sent le SEO.
A LA PLACE : aller direct au repo cite, ou rester sur les sources canoniques de la table.

---

## Commande slash associee

La commande `/recherche-sources` invoque ce skill avec un mot-cle :

```
/recherche-sources                          → propose les 5 categories
/recherche-sources MTEB benchmark           → ouvre directement la categorie recherche
/recherche-sources thread Qwen fine-tune    → ouvre directement la categorie communaute
```

Fichier : `~/.claude/commands/recherche-sources.md`.

---

## Additional Resources

### Reference Files
- **`references/sources-code-repos.md`** — Templates de requete GitHub, Sourcegraph, GitLab, Codeberg + pieges
- **`references/sources-communaute.md`** — Reddit, HN, Lobsters, forums OpenAI/Anthropic/HuggingFace, Discord, Stack Overflow + pieges
- **`references/sources-recherche-ia.md`** — arXiv, Papers with Code, OpenReview, Semantic Scholar, HuggingFace (models + datasets + MTEB), Replicate, Ollama + pieges
- **`references/sources-veille.md`** — Newsletters, blogs editeurs, podcasts IA + pieges
