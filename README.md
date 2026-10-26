# DSA 4060 – Personalized Movie Recommender

**Student Name:** Samantha Masaki Nyatichi  
**Student ID:** 670455  
**Assigned User ID:** 16  
**Course:** DSA 4060 – Recommender Systems

## 1. Project Overview

This project develops a content-based movie recommendation system using Python. It analyzes the movie ratings of an assigned user and recommends five movies based on genre similarity.

The project focuses exclusively on **User ID 16**, calculated using the assignment formula:

\[
(55 \bmod 40) + 1 = 16
\]

The recommender uses movie genres and cosine similarity to identify movies that resemble those the user rated positively.

## 2. Project Objectives

- Load and inspect the movie and ratings datasets.
- Analyze User 16's rating history and highest-rated movies.
- Identify patterns in the user's genre preferences.
- Convert movie genres into numerical features.
- Calculate genre similarity using cosine similarity.
- Recommend five movies that User 16 has not already rated.
- Explain the recommendations and discuss the system's limitations.

## 3. Tools and Technologies

- **Python** – implementation and analysis.
- **Pandas** – data loading, filtering, merging, and summarization.
- **Scikit-learn** – feature extraction and similarity calculations.
- **CountVectorizer** – converting movie genres into binary numerical features.
- **Cosine similarity** – comparing movie genre profiles.
- **Jupyter Notebook** – executing and documenting the project.

## 4. Dataset Description

The project uses two CSV files.

| Dataset | Description |
|---|---|
| `movies.csv` | Contains movie IDs, titles, and genre labels. |
| `ratings.csv` | Contains user IDs, movie IDs, and rating scores. |

The notebook reports **36 movies with 3 columns** and **440 ratings with 3 columns**. Its initial missing-value checks report no missing values in either dataset.

## 5. Methodology

### 5.1 Data Loading and Inspection

The datasets are loaded using Pandas. The notebook examines their first five rows, dimensions, column structure, and missing values.

### 5.2 User Profile Analysis

The ratings are filtered to include only User ID 16. The ratings are joined with the movie catalogue to display the titles, genres, and ratings of the movies the user has watched.

The notebook identifies ten rated movies. Arrival and Hidden Figures received the highest ratings, at 4.0 each.

### 5.3 Genre Preference Analysis

The genre labels are separated so that movies with multiple genres contribute to each relevant genre's summary. Average ratings and the number of movies rated within each genre are calculated.

Biography has an average rating of 4.00 based on one movie, Drama averages 3.60 across five movies, and Sci-Fi averages 3.50 across four movies. These results should be interpreted cautiously because some genres have limited observations.

### 5.4 Content-Based Filtering

Movies rated **4.0 or higher** are treated as positive examples of the user's interests. For User 16, these movies are Arrival and Hidden Figures.

`CountVectorizer` converts the genre labels into binary feature vectors. Cosine similarity is then calculated between movies based on their genre representations.

The recommender scores each candidate by averaging its similarity to the positively rated movies. It also records the closest positively rated movie to help explain each recommendation.

### 5.5 Recommendation Selection

All movies already rated by User 16 are excluded from the candidate list. The remaining movies are ranked by their average similarity score, closest-match similarity, and title.

The system selects five unique, previously unrated movies and validates that the recommendations satisfy the assignment requirements.

## 6. Recommended Movies

The notebook produces the following recommendations:

| Rank | Recommended Movie | Genres | Reason |
|---:|---|---|---|
| 1 | Interstellar | Sci-Fi, Drama | Shares Sci-Fi and Drama genres with Arrival, rated 4.0. |
| 2 | The Pursuit of Happyness | Drama, Biography | Shares Drama and Biography genres with Hidden Figures, rated 4.0. |
| 3 | The Social Network | Drama, Biography | Shares Drama and Biography genres with Hidden Figures, rated 4.0. |
| 4 | Creed | Sports, Drama | Shares Drama with Arrival; cosine similarity to the closest match is 0.50. |
| 5 | Moneyball | Sports, Drama | Shares Drama with Arrival; cosine similarity to the closest match is 0.50. |

The results are based on genre similarity rather than a prediction of the exact rating the user would give each movie.

## 7. Validation

The notebook includes checks to confirm that:

- The assigned User ID is 16.
- Exactly five recommendations are generated.
- The recommended movie IDs are unique.
- None of the recommended movies has already been rated by User 16.

These checks help ensure that the output meets the main requirements of the practical quiz.

## 8. Limitations and Improvements

### Limitation

The recommender relies only on genre labels. It cannot capture differences in story, quality, actors, or other characteristics between movies that share similar genres. The relatively small movie catalogue may also limit the variety of recommendations.

### Suggested Improvement

A hybrid recommendation system could combine content-based filtering with collaborative filtering. Genre similarity would connect recommendations to the user's known interests, while collaborative filtering could use rating patterns from users with similar preferences.

## 9. How to Run the Project

1. Download or clone the project repository.
2. Ensure Python is installed.
3. Install the required libraries:

   ```bash
   pip install pandas scikit-learn jupyter
   ```

4. Place `movies.csv` and `ratings.csv` in the project root or in a folder named `data`.
5. Open a terminal in the project directory and run:

   ```bash
   jupyter notebook DSA4060_Recommender_670455.ipynb
   ```

6. Run the notebook cells in order, from the beginning to the final validation checks.

## 10. Repository Structure

```text
DSA4060-Recommender-670455/
├── DSA4060_Recommender_670455.ipynb
├── movies.csv
├── ratings.csv
└── README.md
```

## 11. Conclusion

This project demonstrates how content-based filtering can support personalized movie recommendations. By analyzing User 16's rating history, extracting genre features, calculating cosine similarity, and excluding previously rated movies, the system generates five recommendations with explanations.

The project also demonstrates the importance of validating recommendation outputs and recognizing the limitations of using genre information alone.