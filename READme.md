{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Python Special (Dunder) Methods\n",
    "\n",
    "\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "---\n",
    "## 1. `__init__` — The Initializer\n",
    "Runs automatically when a new object is created.\n",
    "Use it to assign starting values to the object's attributes."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "class Student:\n",
    "    def __init__(self, name, student_id, level):\n",
    "        self.name       = name\n",
    "        self.student_id = student_id\n",
    "        self.level      = level\n",
    "\n",
    "s1 = Student('Leslie Owusu', 'UMaT/EL/24/001', 100)\n",
    "print('Name   :', s1.name)\n",
    "print('ID     :', s1.student_id)\n",
    "print('Level  :', s1.level)\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "---\n",
    "## 2. `__str__` and `__repr__` — String Representations\n",
    "- `__str__` gives a **user-friendly** description (used by `print`).\n",
    "- `__repr__` gives a **developer-friendly** description used for debugging.\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "class Student:\n",
    "    def __init__(self, name, student_id, level):\n",
    "        self.name       = name\n",
    "        self.student_id = student_id\n",
    "        self.level      = level\n",
    "\n",
    "    def __str__(self):\n",
    "        return f'{self.name} (Level {self.level}) — ID: {self.student_id}'\n",
    "\n",
    "    def __repr__(self):\n",
    "        return f\"Student('{self.name}', '{self.student_id}', {self.level})\"\n",
    "\n",
    "s1 = Student('Ama Boateng', 'UMaT/EL/24/002', 100)\n",
    "print(str(s1))\n",
    "print(repr(s1))\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "---\n",
    "## 3. `__len__` — Defining Length\n",
    "Called when `len()` is used on an object. Must return an integer."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "class ClassGroup:\n",
    "    def __init__(self, students):\n",
    "        self.students = students\n",
    "\n",
    "    def __len__(self):\n",
    "        return len(self.students)\n",
    "\n",
    "el1a = ClassGroup(['Leslie', 'Ama', 'Kofi', 'Abena', 'Yaw'])\n",
    "print('Students in EL 1A:', len(el1a))\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "---\n",
    "## 4. `__eq__` — Equality Comparison\n",
    "Defines what `==` means between two objects of your class."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "class Student:\n",
    "    def __init__(self, name, student_id):\n",
    "        self.name       = name\n",
    "        self.student_id = student_id\n",
    "\n",
    "    def __eq__(self, other):\n",
    "        return self.student_id == other.student_id\n",
    "\n",
    "s1 = Student('Leslie Owusu',        'UMaT/EL/24/001')\n",
    "s2 = Student('L. Owusu (updated)',  'UMaT/EL/24/001')\n",
    "s3 = Student('Kofi Mensah',         'UMaT/EL/24/003')\n",
    "\n",
    "print('s1 == s2:', s1 == s2)\n",
    "print('s1 == s3:', s1 == s3)\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "---\n",
    "## 5. Operator Overloading — `__add__`, `__sub__`, `__mul__`\n",
    "Let custom objects respond naturally to `+`, `-`, and `*`."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "class DataBundle:\n",
    "    def __init__(self, gigabytes):\n",
    "        self.gigabytes = gigabytes\n",
    "\n",
    "    def __add__(self, other):\n",
    "        return DataBundle(self.gigabytes + other.gigabytes)\n",
    "\n",
    "    def __sub__(self, other):\n",
    "        return DataBundle(self.gigabytes - other.gigabytes)\n",
    "\n",
    "    def __mul__(self, factor):\n",
    "        return DataBundle(self.gigabytes * factor)\n",
    "\n",
    "    def __str__(self):\n",
    "        return f'{self.gigabytes:.1f} GB'\n",
    "\n",
    "weekly_bundle = DataBundle(5.0)\n",
    "used_today    = DataBundle(1.5)\n",
    "print('Remaining after today :', weekly_bundle - used_today)\n",
    "print('Double the bundle     :', weekly_bundle * 2)\n",
    "print('Combined bundles      :', weekly_bundle + used_today)\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "---\n",
    "## 6. `__getitem__` — Index/Key Access\n",
    "Allows bracket-notation reads: `obj[index]`."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "class Timetable:\n",
    "    def __init__(self, courses):\n",
    "        self.courses = courses\n",
    "\n",
    "    def __getitem__(self, index):\n",
    "        return self.courses[index]\n",
    "\n",
    "tt = Timetable(['Engineering Mechanics', 'Electronics', 'Mathematics', 'Workshop Practice'])\n",
    "print('First class :', tt[0])\n",
    "print('Last class  :', tt[-1])\n",
    "print('Slice       :', tt[1:3])\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "---\n",
    "## 7. `__setitem__` — Index/Key Assignment\n",
    "Called when you write `obj[key] = value`."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "class GradeBook:\n",
    "    def __init__(self):\n",
    "        self.grades = {}\n",
    "\n",
    "    def __setitem__(self, course, score):\n",
    "        self.grades[course] = score\n",
    "\n",
    "    def __getitem__(self, course):\n",
    "        return self.grades.get(course, 'Not graded')\n",
    "\n",
    "gb = GradeBook()\n",
    "gb['Electronics']          = 78\n",
    "gb['Engineering Mechanics'] = 84\n",
    "print('Electronics score          :', gb['Electronics'])\n",
    "print('Engineering Mechanics score:', gb['Engineering Mechanics'])\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "---\n",
    "## 8. `__contains__` — Membership Testing\n",
    "Powers the `in` keyword for custom objects."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "class Syllabus:\n",
    "    def __init__(self, topics):\n",
    "        self.topics = topics\n",
    "\n",
    "    def __contains__(self, topic):\n",
    "        return topic in self.topics\n",
    "\n",
    "electronics_syllabus = Syllabus(['BJT Transistors', 'Diodes', 'Operational Amplifiers', 'Logic Gates'])\n",
    "print('\"Diodes\" on syllabus?       ', 'Diodes' in electronics_syllabus)\n",
    "print('\"Quantum Computing\" on syllabus?', 'Quantum Computing' in electronics_syllabus)\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "---\n",
    "## 9. `__call__` — Making Objects Callable\n",
    "Lets you use an object like a function: `obj()`."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "class GradeCurve:\n",
    "    def __init__(self, bonus_points):\n",
    "        self.bonus_points = bonus_points\n",
    "\n",
    "    def __call__(self, raw_score):\n",
    "        return min(100, raw_score + self.bonus_points)\n",
    "\n",
    "mild_curve  = GradeCurve(5)\n",
    "big_curve   = GradeCurve(12)\n",
    "\n",
    "score = 68\n",
    "print(f'Raw score      : {score}')\n",
    "print(f'After mild curve: {mild_curve(score)}')\n",
    "print(f'After big curve : {big_curve(score)}')\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "---\n",
    "## 10. `__iter__` and `__next__` — Custom Iteration\n",
    "Together these two methods make an object usable in a `for` loop.\n",
    "- `__iter__` returns the iterator object (usually `self`).\n",
    "- `__next__` returns the next value, or raises `StopIteration` when done."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "class SemesterWeeks:\n",
    "    \"\"\"Iterates over week numbers from start to end (inclusive).\"\"\"\n",
    "    def __init__(self, start, end):\n",
    "        self.current = start\n",
    "        self.end     = end\n",
    "\n",
    "    def __iter__(self):\n",
    "        return self\n",
    "\n",
    "    def __next__(self):\n",
    "        if self.current > self.end:\n",
    "            raise StopIteration\n",
    "        value = self.current\n",
    "        self.current += 1\n",
    "        return value\n",
    "\n",
    "print('Weeks until mid-semester exams:')\n",
    "for week in SemesterWeeks(1, 7):\n",
    "    print(f'  Week {week}')\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "---\n",
    "## 11. `__bool__` — Boolean Evaluation\n",
    "Called when an object is tested with `if obj:` or `bool(obj)`.\n",
    "Must return `True` or `False`."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "class MomoWallet:\n",
    "    def __init__(self, owner, balance):\n",
    "        self.owner   = owner\n",
    "        self.balance = balance\n",
    "\n",
    "    def __bool__(self):\n",
    "        return self.balance > 0\n",
    "\n",
    "    def __str__(self):\n",
    "        return f'{self.owner} (GHS {self.balance:.2f})'\n",
    "\n",
    "wallet1 = MomoWallet('Leslie', 45.50)\n",
    "wallet2 = MomoWallet('Kofi', 0.00)\n",
    "\n",
    "for wallet in [wallet1, wallet2]:\n",
    "    status = 'HAS FUNDS' if wallet else 'EMPTY'\n",
    "    print(f'{wallet} -> {status}')\n",
    "\n",
    "print('bool(wallet1):', bool(wallet1))\n",
    "print('bool(wallet2):', bool(wallet2))\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "---\n",
    "## 12. `__del__` — Destructor / Cleanup\n",
    "Called when an object is deleted or garbage-collected.\n",
    "Useful for releasing resources such as file handles or network connections."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "class LabSession:\n",
    "    def __init__(self, student_name):\n",
    "        self.student_name = student_name\n",
    "        print(f'[Lab started] Welcome to the electronics lab, {self.student_name}!')\n",
    "\n",
    "    def __del__(self):\n",
    "        print(f'[Lab ended]   Bench powered down. See you next week, {self.student_name}.')\n",
    "\n",
    "session = LabSession('Leslie Owusu')\n",
    "print('... measuring transistor characteristics ...')\n",
    "del session\n"
   ]
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "name": "python",
   "version": "3.10.0"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 4
}
