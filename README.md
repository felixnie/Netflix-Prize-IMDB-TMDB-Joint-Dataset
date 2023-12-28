# Netflix Prize IMDB TMDB Joint Dataset

Your (all-in-one) Netflix Prize dataset, augmented and calibrated with IMDB and TMDB. Refining and updating from time to time.

![sources](https://raw.githubusercontent.com/felixnie/img/main/netflix-prize-01.png)

# Why joint dataset?

- The prestigious Netflix Prize dataset only hosts ratings, titles and release years, while larger datasets have rich information on the genres and credits.

- While aligning movies and TV shows in the Netflix Prize dataset, it's impractical to simply find the matching year and title because:

    - the years may correspond to the release of DVD rather than the theatre release.

    - the titles are slightly different between datasets.

- More and more open datasets are becoming private, making the old scraping methods deprecated.

- The scraping scripts for augmentation can be applied to other datasets. See my [other datasets](#other-datasets).

# What's included?

## 1. Netflix Prize - IMDB joint dataset

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

Movies with scores lower than 0.3 are dropped.

### Completeness

| Netflix Prize - IMDB | Netflix Prize - TMDB |
| :------------------: | :------------------: |
| ![](https://raw.githubusercontent.com/felixnie/img/main/netflix-prize-02.png) | ![](https://raw.githubusercontent.com/felixnie/img/main/netflix-prize-04.png) |
| ![](https://raw.githubusercontent.com/felixnie/img/main/netflix-prize-03.png) | ![](https://raw.githubusercontent.com/felixnie/img/main/netflix-prize-05.png) |

## 2. Netflix Prize - TMDB joint dataset

Similar to the above.

## 3. Netflix Prize - IMDB genres

## 4. Netflix Prize - TMDB genres

## 5. Netflix Prize - IMDB credits

## 6. Netflix Prize - TMDB credits

# Other datasets

MovieLens IMDB TMDB Joint Dataset

