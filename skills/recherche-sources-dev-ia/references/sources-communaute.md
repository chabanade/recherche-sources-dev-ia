# Sources Communaute & Forums — Templates de requete

Documentation chargee a la demande par le skill `recherche-sources-dev-ia`.

---

## Reddit

URL : https://www.reddit.com

### Subreddits utiles (cible IA / dev)

| Subreddit | Focus | Quand y aller |
|-----------|-------|---------------|
| r/LocalLLaMA | LLM open-source, fine-tuning, hardware | Modeles locaux, GPU, quantization |
| r/MachineLearning | Recherche IA academique | Papiers, methodes, debats theoriques |
| r/LangChain | Framework LangChain | Bugs, patterns, retours d'experience |
| r/ClaudeAI | Anthropic Claude | Tips Claude Code, plugins, hacks |
| r/OpenAI | OpenAI GPT, Assistants | Tarif, bugs, releases |
| r/ChatGPTPro | Pro tips, prompting | Workflow utilisateur pro |
| r/Programming | Dev general | Tendances dev hors IA |
| r/dataengineering | Data eng, pipelines | ETL, vector DB, infra |

### Templates copiables

Recherche ciblee site:reddit.com via Google :
```
site:reddit.com/r/LocalLLaMA "Qwen 3" "fine-tune"
```

Sur Reddit natif (champ search) :
```
subreddit:LocalLLaMA "rerank" sort:top time:month
```

### Piege connu

INTERDIT : citer un post Reddit a 5 upvotes comme reference.
A LA PLACE : filtrer `sort:top time:month` et lire les commentaires top (souvent + utiles que le post).

INTERDIT : prendre un post sans flair pour un consensus.
A LA PLACE : preferer les posts avec flair `Discussion`, `Research`, `News`, et ignorer les flairs `Question`, `Help`, `Funny`.

Confiance par defaut : 60% si upvotes > 100 et commentaires riches. 30% si post isole.

---

## HackerNews

URL : https://news.ycombinator.com
Recherche : https://hn.algolia.com

### Templates copiables

Algolia search :
```
"vector database" 100..500 points 2026
```

Filtres Algolia :
- `points:>100` (qualite)
- `2025-12-01..2026-05-01` (plage de dates)
- `author:dang` (auteur specifique)

### Piege connu

INTERDIT : ignorer les commentaires sur HN — souvent + riches que l'article.
A LA PLACE : lire le thread des commentaires top en parallele de l'article.

Confiance par defaut : 65% pour les posts > 100 points avec commentaires nourris.

---

## Lobsters

URL : https://lobste.rs

Communaute plus petite, plus selective, focus dev/infra. Moins de bruit que HN.

### Piege connu

INTERDIT : utiliser Lobsters pour de la veille generaliste IA grand public.
A LA PLACE : Lobsters pour le dev pointu (langages, OS, infra), HN pour la culture tech, Reddit pour les communautes specifiques.

---

## Forum officiel OpenAI

URL : https://community.openai.com

### Quand y aller

- Bugs API GPT / Assistants
- Tarification, quotas, rate limits
- Recettes prompting communes
- Annonces produits (parfois plus a jour que le blog officiel)

### Piege connu

INTERDIT : citer un post community.openai.com comme s'il etait normatif (= doc officielle).
A LA PLACE : prefixer "post forum community" + si possible verifier sur https://platform.openai.com/docs.

Confiance par defaut : 70% pour les posts d'employes OpenAI (badge staff), 50% pour les posts utilisateurs.

---

## Doc Anthropic + forum

URL doc : https://docs.anthropic.com
URL forum : https://support.anthropic.com (centre d'aide officiel)

Pour Claude Code specifiquement : https://docs.claude.com/en/docs/claude-code

### Quand y aller

- API Claude (messages, tool use, prompt caching, batch)
- Claude Code (CLI, hooks, MCP, skills, slash commands)
- Limites, tarifs, quotas

Confiance par defaut : 95% (source normative).

---

## HuggingFace Forums

URL : https://discuss.huggingface.co

### Quand y aller

- Transformers library (modeles, tokenizers)
- Datasets, training, fine-tuning
- Spaces (deploiement gratuit demo)
- Probleme specifique avec un modele

### Piege connu

INTERDIT : confondre un thread du forum avec la doc officielle huggingface.co/docs.
A LA PLACE : preferer https://huggingface.co/docs pour la verite normative.

Confiance par defaut : 70% pour les posts staff HF, 55% pour les utilisateurs.

---

## Discord LangChain

URL : https://discord.gg/langchain

Tres actif, retours d'experience temps reel. Mais ephemere (les threads disparaissent dans le scroll).

### Piege connu

INTERDIT : citer un message Discord comme source.
A LA PLACE : capturer la version recroisee sur GitHub Discussions ou le forum officiel.

Confiance par defaut : 50% (chat ephemere).

---

## Stack Overflow

URL : https://stackoverflow.com

### Tags utiles

- [anthropic-claude]
- [langchain]
- [llama-index]
- [openai-api]
- [llm]
- [vector-database]
- [retrieval-augmented-generation]

### Templates copiables

Recherche par tag + filtre score :
```
[anthropic-claude] is:answer score:5 2026
```

### Piege connu

INTERDIT : copier une reponse Stack Overflow sans regarder la date.
A LA PLACE : verifier que la reponse est posterieure a la derniere release majeure (ex : Claude Code v1.x → ignorer les reponses pre-2026).

Confiance par defaut : 75% pour les reponses accepted + score > 10. 50% sinon.
