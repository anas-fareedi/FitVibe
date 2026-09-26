# Fit_Vibe - Fitness Agent

Fitness Agent is a FastAPI service that analyzes a user's fitness profile and returns a structured fitness plan, including workouts, meals, macro guidance, and motivation.

## Technologies

- Python
- FastAPI
- Uvicorn
- Pydantic
- pydantic-ai
- python-dotenv
- Gemini (`gemini-2.5-flash` via `pydantic-ai`)

## Project Structure

```text
app/
  main.py
  fitness_advisor/
    controller.py
    service.py
    model.py
requirements.txt
```

## Setup

1. Create and activate a virtual environment.
2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. Add your AI provider credentials to a `.env` file.

## Run the API

From the repository root:

```bash
uvicorn app.main:app --reload
```

The API will start on `http://127.0.0.1:8000`.

## API

### `POST /analyze`

Accepts a fitness profile and returns a structured fitness recommendation.

Example request body:

```json
{
  "age": 29,
  "weight": 72.5,
  "height": 175,
  "gender": "male",
  "activity_level": "moderate",
  "fitness_goal": "gain_muscle",
  "dietary_restrictions": [],
  "injuries": [],
  "preferred_workout_time": "morning",
  "available_equipment": ["dumbbells", "mat"],
  "workout_days_per_week": 4
}
```

Response includes:
- `workout_plan`
- `meal_plan`
- `daily_calories`
- `macros`
- `tips`
- `weekly_schedule`
- `motivation_quote`
