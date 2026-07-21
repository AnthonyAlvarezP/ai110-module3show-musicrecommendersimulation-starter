# 🎵 Music Recommender Simulation

## Project Summary

In this project you will build and explain a small music recommender system.

Your goal is to:

- Represent songs and a user "taste profile" as data
- Design a scoring rule that turns that data into recommendations
- Evaluate what your system gets right and wrong
- Reflect on how this mirrors real world AI recommenders

Replace this paragraph with your own summary of what your version does.

---

## How The System Works

Explain your design in plain language.

Some prompts to answer:

- What features does each `Song` use in your system
  - For example: genre, mood, energy, tempo

  The features 'Song' uses in my system are genre, mood, energy, tempo, valence, danceability, and acousticness.

- What information does your `UserProfile` store

  The information 'UserProfile' in my system will store favorite genre, mood, targeted energy, and wheter they like acoustic or not.

- How does your `Recommender` compute a score for each song

  My recommender will compute a score for each song by looking at their user profile and doing 1 minus the difference in energy, genre, mood, and acoustic score. Then adding all the scores into a total and determining what is a better match.

- How do you choose which songs to recommend

I will make a total_score and whichever has a higher total_score will be recommended next.

You can include a simple diagram or bullet list if helpful.

---

## Getting Started

### Setup

1. Create a virtual environment (optional but recommended):

   ```bash
   python -m venv .venv
   source .venv/bin/activate      # Mac or Linux
   .venv\Scripts\activate         # Windows

2. Install dependencies

```bash
pip install -r requirements.txt
```

3. Run the app:

```bash
python -m src.main
```

### Running Tests

Run the starter tests with:

```bash
pytest
```

You can add more tests in `tests/test_recommender.py`.

---

## Sample Recommendation Output

Paste a sample of your recommender's output here as a text block so a reader can see what it produces:

```
User profile: genre=pop, mood=happy energy= 0.8
Top Recommendations
========================================
1. Sunrise City - Neon Echo (Score: 5.96)
   Reasons: genre match (+2.0), mood match (+1.0), energy similarity (+1.96), acoustic preference match (+1.0)
----------------------------------------
2. Gym Hero - Max Pulse (Score: 4.74)
   Reasons: genre match (+2.0), energy similarity (+1.74), acoustic preference match (+1.0)
----------------------------------------
3. Rooftop Lights - Indigo Parade (Score: 3.92)
   Reasons: mood match (+1.0), energy similarity (+1.92), acoustic preference match (+1.0)
----------------------------------------
4. Neon Warehouse - Pulse Fracture (Score: 2.90)
   Reasons: energy similarity (+1.90), acoustic preference match (+1.0)
----------------------------------------
5. Night Drive Loop - Neon Echo (Score: 2.90)
   Reasons: energy similarity (+1.90), acoustic preference match (+1.0)

**Screenshot or video** *(optional)*: <!-- Insert a screenshot or demo video link here -->

---

## Experiments You Tried

Use this section to document the experiments you ran. For example:

- What happened when you changed the weight on genre from 2.0 to 0.5
- What happened when you added tempo or valence to the score
- How did your system behave for different types of users

---

## Limitations and Risks

Summarize some limitations of your recommender.

Examples:

- It only works on a tiny catalog
- It does not understand lyrics or language
- It might over favor one genre or mood

You will go deeper on this in your model card.

---

## Reflection

Read and complete `model_card.md`:

[**Model Card**](model_card.md)

Write 1 to 2 paragraphs here about what you learned:

- about how recommenders turn data into predictions
- about where bias or unfairness could show up in systems like this



