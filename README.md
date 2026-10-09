# Grade Calculator

A command-line grade calculator written in Python. It was built as a beginner-friendly project to practice **conditional statements** (`if` / `elif` / `else`), **functions**, **return values**, and **input validation**.

## Features

- Converts numeric scores (0-100) into letter grades (A-F)
- Gives a short remark and a Pass/Fail status for each score
- Calculates the average of all scores entered and the overall grade
- Rejects non-numeric input and scores outside 0-100 without crashing
- Built-in tests that need no extra libraries

## Grading Scale

| Score | Grade |
|---|---|
| 90 - 100 | A |
| 80 - 89 | B |
| 70 - 79 | C |
| 60 - 69 | D |
| Below 60 | F |

A score of 60 or above counts as a pass.

## Requirements

- Python 3.6 or newer (uses f-strings)
- No third-party packages

## Getting Started

Clone the repository and run the program:

```bash
git clone https://github.com/<your-username>/grade-calculator.git
cd grade-calculator
python grade_calculator.py
```

## Usage

Enter scores one at a time and type `done` when you are finished:

```
Grade Calculator
Enter scores one at a time. Type "done" when finished.

Score (0-100) or "done": 85
Grade: B | Pass | Good job.
Score (0-100) or "done": 55
Grade: F | Fail | Failed. Keep practicing.
Score (0-100) or "done": abc
Please enter a valid number.
Score (0-100) or "done": 120
Score must be between 0 and 100.
Score (0-100) or "done": 95
Grade: A | Pass | Excellent work!
Score (0-100) or "done": done

Scores entered: 3
Average: 78.3
Overall grade: C
```

Invalid entries ("abc" and 120 above) are rejected and are not counted in the average.

## Using the functions in your own code

```python
from grade_calculator import get_grade, get_remark, is_passing, calculate_average

print(get_grade(85))                      # B
print(get_remark('B'))                    # Good job.
print(is_passing(55))                     # False
print(calculate_average([80, 90, 100]))   # 90.0
```

## Running the Tests

```bash
python grade_calculator.py --test
```

Expected output:

```
PASS  test_grade_boundaries
PASS  test_grade_invalid
PASS  test_remarks
PASS  test_is_passing
PASS  test_average

5/5 tests passed
```

The test functions follow the `test_` naming convention, so they also work with pytest:

```bash
pip install pytest
pytest grade_calculator.py
```

## Project Structure

```
grade-calculator/
├── grade_calculator.py   # Grading functions, interactive loop, and tests
└── README.md
```

## How It Works

| Function | Purpose |
|---|---|
| `get_grade(score)` | Returns A-F using an `if/elif/else` chain, or `'Invalid'` if the score is outside 0-100 |
| `get_remark(grade)` | Returns a short comment for a letter grade |
| `is_passing(score)` | Returns `True` if the score is 60-100 |
| `calculate_average(scores)` | Returns the average, or `None` for an empty list |
| `main()` | Runs the interactive loop and prints the summary |

The order of conditions in `get_grade` matters. The invalid-range check comes first, then the highest threshold (90) down to the lowest. Checking `score >= 60` first would make every passing score a D.

## Concepts Demonstrated

- `if` / `elif` / `else` chains
- Comparison operators and chained comparisons (`60 <= score <= 100`)
- Logical operators (`or`)
- Functions with parameters and `return` values
- `try` / `except` for input validation
- `while` loops with `break` and `continue`
- Testing with `assert`

## Ideas for Extending the Project

- Add plus and minus grades (B+, B-)
- Weight scores by assignment type (exams count more than quizzes)
- Track scores per subject using a dictionary
- Save and load results from a CSV or JSON file
- Show the highest and lowest scores
- Rewrite the tests with `unittest` or `pytest`

## License

This project is licensed under the MIT License. Feel free to use it for learning.
