# 🎧 Model Card: Music Recommender Simulation

## 1. Model Name  

Give your model a short, descriptive name.  
Example: **VibeFinder 1.0**  

Recommender3000

---

## 2. Intended Use  

Describe what your recommender is designed to do and who it is for. 

Prompts:  

- What kind of recommendations does it generate 

So there is a csv file that contains songs. Depending on the user preference, the recommender3000 will determine what song is best from the list to play next. 

- What assumptions does it make about the user

Depending on the user prefence, it will assume what type of music you like and recommends songs with explainations.

- Is this for real users or classroom exploration  
This is a classroom exploration.
---

## 3. How the Model Works  

Explain your scoring approach in simple language.  

Prompts:  

- What features of each song are used (genre, energy, mood, etc.) 

user_pref uses genre, acoustic, mood, and energy prefence to score to determine list ranking.

- What user preferences are considered

* Genre
* mood
* energy
* acoustic

- How does the model turn those into a score  

Compute a score for each song by looking at their user profile and doing 1 minus the difference in energy, genre, mood, and acoustic score. Then adding all the scores into a total and determining what is a better match.

- What changes did you make from the starter logic  

I don't think I changed anything.

Avoid code here. Pretend you are explaining the idea to a friend who does not program.

---

## 4. Data  

Describe the dataset the model uses.  

Prompts:  

- How many songs are in the catalog 

There are 18 in the catalog.

- What genres or moods are represented  

Genres:
* pop
* metal
* rap
* etc ...

Moods:
* happy
* sad
* neutral

- Did you add or remove data

I added 8 new songs to the csv.

- Are there parts of musical taste missing in the dataset  

Yes, there are some missing.

---

## 5. Strengths  

Where does your system seem to work well  

Prompts:  

- User types for which it gives reasonable results

* I found that user profiles that do not contradict each other like (mood: happy and low energy) tend to work the best.

- Any patterns you think your scoring captures correctly  

* A pattern I found is that some songs show up more than others even if the're not similar. Almost like if it is being bias to some songs.

- Cases where the recommendations matched your intuition 

User profiles that do not contradict natch more often.

---

## 6. Limitations and Bias 

Where the system struggles or behaves unfairly. 

**Features it does not consider**

* The scorer only looks at genre, mood, energy, and acousticness. `valence`, `tempo_bpm`, and `danceability` are loaded from the CSV but never used, so two songs that are identical on those four fields get the exact same score even if one is a slow ballad and the other is a fast, upbeat track. 

* Acousticness itself is also flattened into a yes/no split at 0.5, so a song at 0.51 counts as "acoustic" the same as a song at 0.95, and there's no way to ask for "somewhat acoustic."

**Genres or moods that are underrepresented**

* Out of 18 songs, 15 different genres are represented, but 13 of them (rock, ambient, jazz, synthwave, indie pop, classical, hip hop, folk, metal, reggae, r&b, house, country) have exactly one song each. Only lofi (3 songs) and pop (2 songs) have more than one. That means a metal or country fan, for example, sees the same single song every time no matter how the rest of their profile changes 

**Cases where the system overfits to one preference**

* Genre match is worth +2.0 out of a max possible 6.0 — more than mood (+1.0) and the acoustic bonus (+1.0) combined. In practice this means stating a favorite genre almost guarantees that genre's song(s) land at the top of the list, even if the energy or mood is a poor fit, because no combination of the other three factors can outweigh a genre mismatch unless energy similarity is also close to perfect. 

**Ways the scoring might unintentionally favor some users**

* The matching on genre and mood is an exact string comparison, so typing "Pop" instead of "pop," or "Happy" instead of "happy," silently loses the match bonus with no error or warning. Users who happen to type preferences in the exact casing/wording used in the dataset get better recommendations than users who phrase things slightly differently, even though both mean the same thing. 

---

## 7. Evaluation  

How you checked whether the recommender behaved as expected. 

Prompts:  

- Which user profiles you tested 

* pop/happy/0.8/False
* pop/sad/0.2/True
* Metel/sad/1/True

- What you looked for in the recommendations  

I looked for whether it matched my own recommendation list that I ranked personally. I then compared them to see if the recommendations were accurate. 

- What surprised you  

* What supprised me the most is how 50/50 my model is.

- Any simple tests or comparisons you ran  
* Case sensitive test
* conflicting mood and energy
No need for numeric metrics unless you created some.

---

## 8. Future Work  

Ideas for how you would improve the model next.  

Prompts:  

- Additional features or preferences  

* I would want to add more to the user prefences like danceabiltly and valence. This will help make it less bias since when one prefence would score 2.0 it would overpower since it is out of 6.0 making that 2.0 a third of the total. 

---

## 9. Personal Reflection  

A few sentences about your experience.  

- How this changed the way you think about music recommendation apps  

During this project, I learned many things about how recommendation apps work. For example, collaborative filtering, using similar people prefernces to recommend you and content-based filtering, anazling what you like to find other things that are similar to what you like.

