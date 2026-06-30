# Python-Special-Methods
A hands-on walkthrough of Python's special ("dunder") methods — the methods that let your own classes work with built-in syntax like print(), len(), ==, +, [], in, and for. Each method is explained briefly and backed by a runnable, real-world-flavored example.

Why dunder methods?

Dunder methods are how Python lets custom objects feel like built-in types. Once you know them, you can write classes that just work with the language instead of needing extra helper functions for everything.

What's inside

#Method(s)What it doesExample used1__init__Initializes a new object's attributesStudent2__str__, __repr__Controls how an object prints / is shown in debuggingStudent3__len__Powers len(obj)ClassGroup4__eq__Defines what == means between two objectsStudent5__add__, __sub__, __mul__Operator overloading (+, -, *)DataBundle6__getitem__Enables obj[index] readsTimetable7__setitem__Enables obj[key] = value writesGradeBook8__contains__Powers the in keywordSyllabus9__call__Makes an object callable like a function: obj()GradeCurve10__iter__, __next__Makes an object usable in a for loopSemesterWeeks11__bool__Controls truthiness in if obj:MomoWallet12__del__Runs cleanup logic when an object is destroyedLabSession
