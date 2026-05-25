# Sources Recherche & Modeles IA — Templates de requete

Documentation chargee a la demande par le skill `recherche-sources-dev-ia`.

---

## arXiv

URL : https://arxiv.org

### Categories utiles

| Category | Focus |
|----------|-------|
| cs.CL | NLP / Language models |
| cs.AI | Intelligence artificielle generale |
| cs.LG | Machine learning (theorie + methodes) |
| cs.IR | Information retrieval (RAG, search) |
| cs.HC | Human-computer interaction (UX IA) |
| stat.ML | Methodes statistiques ML |

### Templates copiables

Recherche full-text arXiv :
```
cat:cs.CL "retrieval augmented" 2026
```

Filtres URL arXiv :
```
https://arxiv.org/search/?searchtype=all&query=cross-encoder+reranker&start=0
```

### Piege connu

INTERDIT : citer un papier arXiv v1 (preprint non revise).
A LA PLACE : verifier qu'il existe une v2 ou v3 (revisions) avant de citer, ou recroiser avec Papers with Code.

INTERDIT : confondre un papier arXiv avec un papier publie en conference (NeurIPS, ICLR, ACL).
A LA PLACE : verifier dans les commentaires arXiv ou via OpenReview si le papier a ete accepte en conference.

Confiance par defaut : 80% si v2+ et auteurs identifiables, 65% si v1 sans cross-validation.

---

## Papers with Code

URL : https://paperswithcode.com

Avantage cle : chaque papier est appaire avec le **code** quand il existe.

### Quand y aller

- Trouver l'implementation reference d'une methode
- Comparer des methodes sur des benchmarks (SOTA tables)
- Trouver des datasets

### Templates copiables

Top papiers RAG :
```
https://paperswithcode.com/search?q=retrieval+augmented+generation
```

Benchmarks reranking :
```
https://paperswithcode.com/task/text-retrieval
```

### Piege connu

INTERDIT : assumer qu'un papier SOTA = la meilleure methode pour ton cas.
A LA PLACE : verifier que le benchmark utilise ressemble a ton corpus (taille, langue, domaine).

Confiance par defaut : 85% (papier + code public ramene le risque).

---

## OpenReview

URL : https://openreview.net

Plateforme officielle pour ICLR, NeurIPS, COLM... Avec les reviews PUBLIQUES.

### Quand y aller

- Lire les reviews d'un papier pour evaluer sa solidite
- Voir les rebuttals de l'auteur
- Suivre les conferences en cours

### Piege connu

INTERDIT : assumer qu'un score eleve OpenReview = papier fiable.
A LA PLACE : lire 2-3 reviews complets pour comprendre les forces ET faiblesses.

Confiance par defaut : 85% si accepte conference, 60% si rejete (mais parfois rejete pour des raisons hors qualite, lire les reviews).

---

## Semantic Scholar

URL : https://www.semanticscholar.org

Moteur scientifique avec graph de citations. Bon pour trouver les papiers qui ont cite un papier donne, et donc voir comment une methode a evolue.

### Templates copiables

Recherche par influence :
```
https://www.semanticscholar.org/search?q=cross+encoder+reranking&sort=influence
```

### Piege connu

INTERDIT : confondre "highly cited" avec "fiable et actuel".
A LA PLACE : verifier les dates des citations, un papier 2020 toujours cite en 2026 est solide.

---

## Connected Papers

URL : https://www.connectedpapers.com

Visualisation du graphe de papiers connectes a un papier seed. Excellent pour explorer un sujet sans en connaitre les references.

### Quand y aller

- Comprendre le contexte autour d'un papier nouveau
- Trouver les ancetres conceptuels d'une methode

### Piege connu

INTERDIT : prendre le graphe pour une carte exhaustive du domaine.
A LA PLACE : utiliser Connected Papers comme entree, puis recroiser avec arXiv et Papers with Code.

---

## Hugging Face — Models

URL : https://huggingface.co/models

### Filtres utiles

```
https://huggingface.co/models?other=text-generation&sort=downloads
```

Filtres URL :
- `?library=transformers`
- `?other=text-generation`
- `?language=fr` (multilingue : preferer aussi `en` et `multilingual`)
- `?sort=downloads` ou `?sort=likes` ou `?sort=modified`

### Piege connu

INTERDIT : prendre un modele HuggingFace au hasard sans verifier la model card.
A LA PLACE : lire la model card complete (training data, eval, license, contamination), puis tester sur 3-5 prompts representatifs avant adoption.

INTERDIT : ignorer la license du modele.
A LA PLACE : verifier (Apache 2.0, MIT, CC-BY, Llama license, custom) avant tout usage commercial.

Confiance par defaut : 80% pour modeles connus (Anthropic, Meta, Mistral, Qwen, Cohere), 50% pour modeles obscurs sans paper.

---

## Hugging Face — Leaderboards & Spaces

| Leaderboard | URL | Quand y aller |
|-------------|-----|---------------|
| MTEB (embeddings) | https://huggingface.co/spaces/mteb/leaderboard | Choisir un modele d'embedding |
| Open LLM Leaderboard | https://huggingface.co/spaces/open-llm-leaderboard/open_llm_leaderboard | Benchmark LLM general |
| Chatbot Arena | https://lmarena.ai | Classement LLM par vote humain |

### Piege connu

INTERDIT : choisir un embedding uniquement sur son score MTEB.
A LA PLACE : verifier la performance sur la langue cible (fr ou multilingual) et le domaine (juridique, technique...).

INTERDIT : prendre le top du leaderboard sans regarder la taille du modele.
A LA PLACE : croiser le score avec le nombre de parametres et la latence d'inference visee.

Confiance par defaut : 85% pour leaderboards officiels (MTEB, Chatbot Arena), 60% pour leaderboards de niche.

---

## Replicate

URL : https://replicate.com/explore

API hostee pour faire tourner des modeles open-source sans installer. Bon pour tester avant d'auto-heberger.

### Piege connu

INTERDIT : assumer que Replicate = self-hosting (c'est un cloud tiers payant).
A LA PLACE : utiliser Replicate pour tester, puis migrer vers vLLM/Ollama si usage en prod.

---

## Ollama Library

URL : https://ollama.com/library

Bibliotheque officielle Ollama pour modeles locaux. Filtre par taille, RAM requise.

### Quand y aller

- Cherche un modele local executable sur ton hardware
- Verifier qu'un modele HF est disponible en GGUF quantifie

### Piege connu

INTERDIT : telecharger un modele 70B sur une machine 16Go RAM.
A LA PLACE : verifier les tailles GGUF (Q4_K_M, Q5_K_M) et le ratio RAM requis avant pull.

Confiance par defaut : 90% (la library est curatee par Ollama).
