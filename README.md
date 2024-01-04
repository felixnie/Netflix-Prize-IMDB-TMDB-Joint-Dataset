# Netflix Prize IMDB TMDB Joint Dataset

![sources](https://raw.githubusercontent.com/felixnie/img/main/netflix-prize-01.png)

# Why joint dataset?

The prestigious Netflix Prize dataset only hosts ratings, titles and release years, while larger datasets have rich information on the genres and credits.

While aligning movies and TV shows in the Netflix Prize dataset, it's impractical to simply find the matching year and title since:

- the years may correspond to the release of DVD rather than the theatre release.

- the titles are slightly different between datasets.

# What's included?

## 1. `netflix_imdb` Netflix Prize-IMDB dataset

### Contents

Netflix Prize dataset with IMDB ids, titles and release years. Each movie or TV show may have multiple matching results. The results are ranked by the confidence scores.

![](https://raw.githubusercontent.com/felixnie/img/main/netflix-prize-06.png)

| columns | descriptions |
| :-----: | :----------: |
| netflix_id | id in Netflix dataset |
| imdb_ids | list of possible IMDB ids, sorted by `imdb_scores` |
| netflix_title | title in Netflix dataset |
| imdb_titles | list of titles arrording to IMDB ids |
| netflix_year | relase year in Netflix dataset |
| imdb_years | list of release years arrording to IMDB ids |
| imdb_scores | similarity between results from IMDB and the item from Netflix | 
| tmdb_ids | corresponding TMDB ids of the IMDB ids, if they have |

### Confidence scores

The `imdb_scores` models the similarity between a record from IMDB and one from Netflix, based on the gap of release years and the similarity of title strings.

$$\frac{similarity(title_{0}, title_{1})}{1.2^{(year_{0} - year_{1})}}$$

Movies with scores `< 0.3` are dropped.

### Completeness

| distribution | completeness |
| :------------------: | :------------------: |
| ![](https://raw.githubusercontent.com/felixnie/img/main/netflix-prize-02.png) | ![](https://raw.githubusercontent.com/felixnie/img/main/netflix-prize-03.png) |

## 2. `netflix_tmdb` Netflix Prize-TMDB dataset

### Contents

Similar to the [above](#1-netflix-prize---imdb-joint-dataset).

### Completeness

| distribution | completeness |
| :------------------: | :------------------: |
| ![](https://raw.githubusercontent.com/felixnie/img/main/netflix-prize-04.png) | ![](https://raw.githubusercontent.com/felixnie/img/main/netflix-prize-05.png) |

## 3. `netflix_imdb_tmdb` Netflix Prize-IMDB-TMDB joint dataset

### Contents

Merged with IMDB and TMDB datasets. The merging rules are:

1. only movies with scores `> 0.8` are accepted.

2. it's skipped if there exist multiple movies with the same highest score, `1.0`.

### Completeness

| distribution | completeness |
| :------------------: | :------------------: |
| ![](https://raw.githubusercontent.com/felixnie/img/main/netflix-prize-07.png) | ![](https://raw.githubusercontent.com/felixnie/img/main/netflix-prize-08.png) |

## 4. `netflix_all` Netflix Prize-IMDB-TMDB joint dataset with genres and cast

### Contents

Merged with IMDB and TMDB datasets and augmented with genres and cast information from both sources.

![](https://raw.githubusercontent.com/felixnie/img/main/netflix-prize-09.png)

### Completeness

| distribution | completeness |
| :------------------: | :------------------: |
| ![](https://raw.githubusercontent.com/felixnie/img/main/netflix-prize-10.png) | ![](https://raw.githubusercontent.com/felixnie/img/main/netflix-prize-11.png) |
