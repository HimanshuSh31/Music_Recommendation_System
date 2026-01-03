# Music Recommendation System

A machine learning-based music recommendation system that suggests songs to users based on two different approaches: **Popularity-based Recommendation** and **Item Similarity-based Recommendation** (Collaborative Filtering).

## Features

- **Popularity-based Recommender**: Recommends the most popular songs based on overall listen counts across all users
- **Item Similarity-based Recommender**: Provides personalized recommendations based on user listening history using collaborative filtering techniques
- **Co-occurrence Matrix**: Builds song similarities based on users who listened to similar songs
- **Data Analysis**: Comprehensive data exploration and visualization of user listening patterns

## Technologies Used

- **Python 3.x**
- **Pandas**: Data manipulation and analysis
- **NumPy**: Numerical computing
- **Jupyter Notebook**: Interactive development and visualization

## Dataset

The project uses two main datasets:

1. **triplets_file.csv** - Contains user listening history with:
   - `user_id`: Unique identifier for each user
   - `song_id`: Unique identifier for each song
   - `listen_count`: Number of times a user listened to a song

2. **song_data.csv** - Contains song metadata with:
   - `song_id`: Unique identifier for each song
   - `title`: Song title
   - `release`: Album/release name
   - `artist_name`: Artist name
   - `year`: Release year

## Installation

1. Clone this repository:
```bash
git clone https://github.com/yourusername/Music_Recommendation_System.git
cd Music_Recommendation_System
```

2. Install required dependencies:
```bash
pip install -r requirements.txt
```

## Usage

### Running the Jupyter Notebook

1. Launch Jupyter Notebook:
```bash
jupyter notebook
```

2. Open `Music Recommendation Project.ipynb`

3. Run all cells to:
   - Load and merge datasets
   - Perform data analysis
   - Train recommendation models
   - Generate recommendations

### Using the Recommender Classes

#### Popularity-based Recommender

```python
import Recommenders as Recommenders

# Create and train the popularity recommender
pr = Recommenders.popularity_recommender_py()
pr.create(song_df, 'user_id', 'song')

# Get recommendations for a user
recommendations = pr.recommend('user_id_here')
print(recommendations)
```

#### Item Similarity-based Recommender

```python
import Recommenders as Recommenders

# Create and train the item similarity recommender
is_model = Recommenders.item_similarity_recommender_py()
is_model.create(song_df, 'user_id', 'song')

# Get personalized recommendations for a user
recommendations = is_model.recommend('user_id_here')
print(recommendations)

# Get similar songs to a given song
similar_songs = is_model.get_similar_items(['Song Name - Artist Name'])
print(similar_songs)
```

## Project Structure

```
Music_Recommendation_System/
│
├── Music Recommendation Project.ipynb   # Main Jupyter notebook with analysis
├── Recommenders.py                      # Recommendation algorithm implementations
├── song_data.csv                        # Song metadata dataset
├── triplets_file.csv                    # User listening history dataset
├── Music Recommendation Project.html    # HTML export of the notebook
├── requirements.txt                     # Python dependencies
├── .gitignore                          # Git ignore file
└── README.md                           # Project documentation
```

## How It Works

### Popularity-based Recommendation
This approach recommends songs that are globally popular across all users. It:
1. Groups songs by total listen counts
2. Ranks songs based on popularity
3. Returns top N most popular songs

**Pros**: Simple, works for new users (cold start problem)  
**Cons**: Same recommendations for all users, no personalization

### Item Similarity-based Recommendation
This approach uses collaborative filtering to find similar songs based on user behavior. It:
1. Constructs a co-occurrence matrix of songs based on users who listened to both
2. Calculates similarity scores between songs
3. Recommends songs similar to what the user has already listened to

**Pros**: Personalized recommendations, discovers patterns in user behavior  
**Cons**: Requires user history, computationally intensive for large datasets

## Future Enhancements

- Add content-based filtering using audio features
- Implement matrix factorization techniques (SVD, ALS)
- Build a web interface using Flask/Streamlit
- Add hybrid recommendation system combining multiple approaches
- Implement real-time recommendation updates

## License

This project is open source and available for educational purposes.

## Author

**Himanshu Sharma**
- LinkedIn: [Himanshu Sharma](https://www.linkedin.com/in/himanshush31/))

## Acknowledgments

- Dataset: Million Song Dataset subset
- Inspiration: Collaborative filtering and recommendation systems research
