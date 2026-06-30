# Python Special Methods

![Python](https://img.shields.io/badge/python-3.10%2B-blue)
![Jupyter](https://img.shields.io/badge/notebook-jupyter-orange)
![Status](https://img.shields.io/badge/status-learning%20notes-success)

A hands-on walkthrough of Python's special ("dunder") methods — the methods that let your own classes work with built-in syntax like `print()`, `len()`, `==`, `+`, `[]`, `in`, and `for`. Each method is explained briefly and backed by a runnable, real-world-flavored example.

## Why dunder methods?

Dunder methods are how Python lets custom objects feel like built-in types. Once you know them, you can write classes that *just work* with the language instead of needing extra helper functions for everything.

## What's inside

| # | Method(s) | What it does | Example used |
|---|-----------|---------------|--------------|
| 1 | `__init__` | Initializes a new object's attributes | `Student` |
| 2 | `__str__`, `__repr__` | Controls how an object prints / is shown in debugging | `Student` |
| 3 | `__len__` | Powers `len(obj)` | `ClassGroup` |
| 4 | `__eq__` | Defines what `==` means between two objects | `Student` |
| 5 | `__add__`, `__sub__`, `__mul__` | Operator overloading (`+`, `-`, `*`) | `DataBundle` |
| 6 | `__getitem__` | Enables `obj[index]` reads | `Timetable` |
| 7 | `__setitem__` | Enables `obj[key] = value` writes | `GradeBook` |
| 8 | `__contains__` | Powers the `in` keyword | `Syllabus` |
| 9 | `__call__` | Makes an object callable like a function: `obj()` | `GradeCurve` |
| 10 | `__iter__`, `__next__` | Makes an object usable in a `for` loop | `SemesterWeeks` |
| 11 | `__bool__` | Controls truthiness in `if obj:` | `MomoWallet` |
| 12 | `__del__` | Runs cleanup logic when an object is destroyed | `LabSession` |

## Getting started

**Requirements**
- Python 3.10+
- Jupyter Notebook or JupyterLab (or VS Code with the Jupyter extension)

**Run it locally**
```bash
git clone https://github.com/boiiinshadows/Python-Special-Methods.git
cd Python-Special-Methods
jupyter notebook
```
Then open `Python_Special_Methods.ipynb` and run the cells top to bottom.

## Project structure
```
Python-Special-Methods/
├── Python_Special_Methods.ipynb   # Main notebook with explanations + examples
└── README.md
```

## A quick taste
```python
class GradeCurve:
    def __init__(self, bonus_points):
        self.bonus_points = bonus_points

    def __call__(self, raw_score):
        return min(100, raw_score + self.bonus_points)

curve = GradeCurve(10)
print(curve(72))  # 82
```

## Contributing

This started as personal study notes, but if you spot an error or want to suggest a clearer example, feel free to open an issue or a pull request.

## License

No license has been set yet — all rights reserved by default. If you'd like others to freely reuse this, consider adding an [MIT License](https://choosealicense.com/licenses/mit/).
