# Gradebook Analyzer

Create a Python program that reads student grades from a CSV file and produces a summary report.

This problem is designed to practice concepts from **CS50P Weeks 0–6**:

- Functions and variables
- Conditionals
- Loops
- Exceptions
- Libraries
- Unit tests
- File I/O

## Learning Objective

Build a command-line Python program that reads grade data, validates it, calculates final scores, assigns letter grades, and generates a class summary.

## Input File

The program should receive the name of a CSV file as a command-line argument.

Example file: `grades.csv`

```csv
name,quiz,project,exam
Alice,85,92,88
Bob,75,80,70
Charlie,95,90,98
David,invalid,85,80
Eve,60,65,70
```

Each student record contains:

- `name`
- `quiz` score
- `project` score
- `exam` score

## Requirements

Write a program called `gradebook.py` that:

1. Accepts the input filename from the command line.
2. Opens and reads the CSV file using Python’s built-in `csv` library.
3. Calculates each valid student’s final score using this formula:

   ```text
   final_score = quiz * 0.2 + project * 0.3 + exam * 0.5
   ```

4. Assigns a letter grade according to this scale:

   | Final Score | Letter Grade |
   |---|---|
   | 90–100 | A |
   | 80–89 | B |
   | 70–79 | C |
   | 60–69 | D |
   | Below 60 | F |

5. Ignores students with invalid or missing scores.
6. Handles errors gracefully:
   - If no filename is provided, print an error message.
   - If the file does not exist, print an error message.
   - If a score is not a valid number, skip that student.
7. Prints every valid student’s final score and letter grade.
8. Prints the class average.
9. Prints the highest-scoring student.
10. Prints the lowest-scoring student.
11. Prints the number of skipped students.

## Expected Output

For the sample input file above, the output should be similar to:

```text
Alice: 88.10 (B)
Bob: 74.50 (C)
Charlie: 95.30 (A)
Eve: 66.50 (D)

Class average: 81.10
Highest: Charlie with 95.30
Lowest: Eve with 66.50
Skipped students: 1
```

The exact formatting may vary slightly, but the required information must be included.

## Required Functions

Your `gradebook.py` file must contain at least these functions:

```python
def calculate_final_score(quiz, project, exam):
    pass


def get_letter_grade(score):
    pass


def read_students(filename):
    pass


def generate_report(students):
    pass
```

You may create additional helper functions if needed.

## Unit Tests

Create a second file called `test_gradebook.py`.

Write tests for:

1. `calculate_final_score`
2. `get_letter_grade`
3. Handling valid and invalid student records
4. Finding the highest-scoring student
5. Finding the lowest-scoring student
6. Calculating the class average

Example tests:

```python
from gradebook import calculate_final_score, get_letter_grade


def test_calculate_final_score():
    assert calculate_final_score(85, 92, 88) == 88.1


def test_get_letter_grade():
    assert get_letter_grade(95) == "A"
    assert get_letter_grade(82) == "B"
    assert get_letter_grade(74) == "C"
    assert get_letter_grade(65) == "D"
    assert get_letter_grade(40) == "F"
```

Run the tests with:

```bash
pytest test_gradebook.py
```

You may also run all tests in the repository with:

```bash
pytest
```

## Suggested Project Structure

```text
gradebook-analyzer/
├── README.md
├── gradebook.py
├── test_gradebook.py
└── grades.csv
```

The starter code file is intentionally empty so that you can write the solution yourself.

## Restrictions

Do not use:

- Classes
- External packages other than `pytest`
- Pandas
- Regular expressions
- Databases

Use only concepts covered in **CS50P Weeks 0–6** and Python’s standard library.

## Optional Extensions

After completing the required functionality, you may add:

- A command-line option for rounding the output.
- Validation for scores outside the range 0–100.
- A count of students in each letter-grade category.
- Exporting the report to a text file.
- Support for additional assignment categories.
