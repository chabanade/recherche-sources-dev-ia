# recherche-sources-dev-ia

Skill [Claude Code](https://docs.claude.com/en/docs/claude-code) qui se déclenche dès que tu cherches une ressource **dev ou IA** (repos GitHub, threads Reddit, papiers arXiv, modèles Hugging Face, forums OpenAI/Anthropic, veille tendances…) — et qui renvoie 3 à 5 sources canoniques **avec leur requête pré-remplie** et un niveau de confiance par défaut.

Né en réponse au fil [Meydeey du 25/05/2026 14:15](https://labo-ia-elite.slack.com/archives/C0B3WF2TAH5) dans le workshop ELITE #01 — base mémorielle.

---

## Ce que ça fait

Quand tu écris dans Claude Code une phrase du genre :

> « cherche un repo GitHub sur les cross-encoders »
> « trouve-moi le leaderboard MTEB »
> « papier arXiv sur RAG retrieval »
> « tendance IA récente sur les agents »

…le skill se charge automatiquement, lit le fichier de référence pertinent (parmi 4), et te sort :

- **3 à 5 URL canoniques** (officielles, pas de site obscur)
- Pour chacune, une **requête pré-remplie copy-paste** avec tes mots-clés
- Un **niveau de confiance par défaut** (45% à 95% selon la source)
- Un **piège connu** à éviter

Tu peux aussi le déclencher manuellement : `/recherche-sources MTEB benchmark`.

---

## 5 catégories couvertes

| Catégorie | Sources principales | Référence |
|-----------|---------------------|-----------|
| **Code & repos** | GitHub Search/Trending, Sourcegraph, GitLab, Codeberg | `sources-code-repos.md` |
| **Communauté & forums** | Reddit (r/LocalLLaMA, r/MachineLearning, r/LangChain, r/ClaudeAI), HackerNews/Algolia, Lobsters, forums OpenAI/Anthropic/HuggingFace, Discord LangChain, Stack Overflow | `sources-communaute.md` |
| **Recherche académique** | arXiv (cs.CL, cs.IR, cs.LG…), Papers with Code, OpenReview, Semantic Scholar, Connected Papers | `sources-recherche-ia.md` |
| **Modèles** | Hugging Face models + leaderboards (MTEB, Open LLM, Chatbot Arena), Replicate, Ollama Library | `sources-recherche-ia.md` |
| **Veille & tendances** | Blogs Anthropic/OpenAI/Mistral/LangChain/LlamaIndex, newsletters (The Batch, AlphaSignal, Latent Space…), podcasts, YouTube | `sources-veille.md` |

---

## Installation (cohorte workshop-01 ou perso)

### 1. Le skill (auto-trigger)

Copie le dossier `skills/recherche-sources-dev-ia/` dans ton plugin Claude Code perso :

```
<ton-plugin>/skills/recherche-sources-dev-ia/
├── SKILL.md
└── references/
    ├── sources-code-repos.md
    ├── sources-communaute.md
    ├── sources-recherche-ia.md
    └── sources-veille.md
```

Claude Code détecte automatiquement les skills via la convention `skills/<nom>/SKILL.md`. Pas de manifeste à éditer.

### 2. La commande slash (optionnel)

Copie `commands/recherche-sources.md` dans `~/.claude/commands/` (Linux/macOS) ou `C:\Users\<toi>\.claude\commands\` (Windows).

Test : `/recherche-sources MTEB benchmark`

---

## Choix techniques

- **`references/` séparées** : le `SKILL.md` (200 lignes) ne charge PAS les 4 références en upfront. Claude lit uniquement la référence pertinente à la demande, pour éviter la pollution de contexte.
- **Format chronologique** : Avant la recherche / Pendant / Après — calqué sur la convention « Meydeey 5 règles d'or » des skills V2 du workshop.
- **Blocs INTERDIT / À LA PLACE** : 9 paires dans le SKILL + une par référence. Format prescriptif (négation + alternative concrète) plutôt que descriptif.
- **Niveau de confiance par défaut** : chaque source a un score (Anthropic docs = 95%, post Reddit isolé = 30%, etc.) à recroiser systématiquement.

---

## Pièges connus du skill (extrait)

> **INTERDIT** : citer un blog éditeur (Anthropic, OpenAI…) comme vérité normative sans recroiser.
> **À LA PLACE** : un blog éditeur est promotionnel → lire d'un œil critique, croiser avec un papier ou un benchmark indépendant.

> **INTERDIT** : choisir un embedding uniquement sur son score MTEB global.
> **À LA PLACE** : filtrer sur la langue cible (FR ou multilingual), le domaine, et croiser taille modèle + latence — le top du leaderboard est souvent un modèle 7B+ ingérable en prod.

---

## Statut & versions

- **v0.1.0 draft** (26/05/2026) — création initiale, 5 catégories, 30+ sources.
- **v0.2.0 prévue** : forcer la date de consultation dans le format de sortie, garde-fou contre l'ajout de sources hors-skill.

---

## Crédits

- **Origine** : proposition de Meydeey, workshop ELITE #01, fil #workshop-01-base-memorielle du 25/05/2026 14:15.
- **Convention V2 (Avant/Pendant/Après + INTERDIT/À LA PLACE)** : Meydeey, plugin `mehdi-skills-plugin`.
- **Auteur de cette implémentation** : Mehdi Chabanade ([@chabanade](https://github.com/chabanade)).

---

## License

[MIT](LICENSE) — fais-en ce que tu veux, mentionne juste la source.
