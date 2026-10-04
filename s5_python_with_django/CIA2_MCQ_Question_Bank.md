# CIA2 Exam Master MCQ Question Bank - Python with Django

**Subject:** Python with Django  
**Pattern:** Multiple Choice Questions (MCQs) with Detailed Explanations  
**Coverage:** 100% Exhaustive Topic Coverage across ALL Units (Units 1 to 3)  

---

## 🐍 Unit 1: Python Core, OOP & Advanced Fundamentals

#### Q1. In Python Object-Oriented Programming, what algorithm determines the Method Resolution Order (MRO) in multiple inheritance?
- (A) Dijkstra's Algorithm
- (B) C3 Linearization Algorithm
- (C) Depth-First Search with Post-Ordering
- (D) Topological Sort with Kahn's Algorithm
**Answer:** (B) C3 Linearization Algorithm  
**Explanation:** Python uses the C3 Linearization algorithm to calculate MRO, ensuring monotonicity and respecting parent class ordering.

#### Q2. What is the output of the following Python code snippet?
```python
def my_decorator(func):
    def wrapper(*args, **kwargs):
        return func(*args, **kwargs) * 2
    return wrapper

@my_decorator
def add(a, b):
    return a + b

print(add(3, 4))
```
- (A) `7`
- (B) `14`
- (C) `TypeError`
- (D) `24`
**Answer:** (B) `14`  
**Explanation:** `@my_decorator` wraps `add(3, 4)` so it computes `(3 + 4) * 2 = 14`.

#### Q3. What is the key functional difference between a Python Generator function (using `yield`) and a regular function returning a list?
- (A) Generator functions execute faster on CPU.
- (B) Generator functions return an iterator that yields items lazily one at a time on demand ($O(1)$ memory), whereas regular functions allocate the entire list in memory ($O(N)$ space).
- (C) Regular functions cannot return numbers.
- (D) Generator functions cannot be iterated over in a `for` loop.
**Answer:** (B) Generator functions return an iterator that yields items lazily one at a time on demand ($O(1)$ memory), whereas regular functions allocate the entire list in memory ($O(N)$ space).  
**Explanation:** `yield` suspends function execution, returning values lazily without constructing the whole list in RAM.

#### Q4. Which Python built-in exception handling block is executed ONLY when NO exception is raised in the `try` block?
- (A) `except`
- (B) `finally`
- (C) `else`
- (D) `raise`
**Answer:** (C) `else`  
**Explanation:** In Python `try-except-else-finally`, the `else` block runs only if the `try` block succeeds without raising any exception. `finally` runs unconditionally.

#### Q5. What is the result of evaluating the slice `lst[1:8:2]` on `lst = [10, 20, 30, 40, 50, 60, 70, 80, 90]`?
- (A) `[20, 40, 60, 80]`
- (B) `[10, 30, 50, 70]`
- (C) `[20, 30, 40, 50]`
- (D) `[30, 50, 70, 90]`
**Answer:** (A) `[20, 40, 60, 80]`  
**Explanation:** `lst[1:8:2]` picks elements from index 1 up to (but excluding) index 8 with step 2 $\implies$ indices 1, 3, 5, 7 $\implies$ values `[20, 40, 60, 80]`.

#### Q6. Which context manager protocol methods must a custom Python class implement to be used with the `with` statement?
- (A) `__init__` and `__del__`
- (B) `__enter__` and `__exit__`
- (C) `__open__` and `__close__`
- (D) `__start__` and `__stop__`
**Answer:** (B) `__enter__` and `__exit__`  
**Explanation:** The `with` statement calls `__enter__()` when entering the context block and `__exit__()` when exiting, guaranteeing resource cleanup even if exceptions occur.

#### Q7. Which Python collection type is mutable, unordered, and contains unique hashable elements only?
- (A) List
- (B) Tuple
- (C) Dictionary
- (D) Set
**Answer:** (D) Set  
**Explanation:** Sets in Python are mutable, unordered collections of distinct, hashable elements.

---

## 🌐 Unit 2: Django Architecture, Views & Templates

#### Q8. In Django's MVT (Model-View-Template) architecture, what is the exact role of the "View"?
- (A) Renders HTML layout and CSS styling directly in the browser.
- (B) Contains business logic that fetches data from Models, processes HTTP requests, and returns HTTP responses or renders Templates.
- (C) Defines database schemas and SQL tables.
- (D) Configures domain routing in web server software like Nginx.
**Answer:** (B) Contains business logic that fetches data from Models, processes HTTP requests, and returns HTTP responses or renders Templates.  
**Explanation:** Model = Data layer, View = Business logic controller, Template = Presentation UI layer.

#### Q9. What is the correct sequence of commands to apply model schema changes to the database in Django?
- (A) `python manage.py migrate` then `python manage.py makemigrations`
- (B) `python manage.py makemigrations` then `python manage.py migrate`
- (C) `python manage.py runserver` then `python manage.py dbupdate`
- (D) `python manage.py sqlmigrate` then `python manage.py collectstatic`
**Answer:** (B) `python manage.py makemigrations` then `python manage.py migrate`  
**Explanation:** `makemigrations` generates migration scripts based on `models.py`, and `migrate` applies those migration scripts to the database.

#### Q10. Which file in a Django project directory contains global project configurations, including `INSTALLED_APPS`, `DATABASES`, `MIDDLEWARE`, and `TEMPLATES`?
- (A) `urls.py`
- (B) `models.py`
- (C) `settings.py`
- (D) `wsgi.py`
**Answer:** (C) `settings.py`  
**Explanation:** `settings.py` is the central configuration module for a Django application environment.

#### Q11. In Django Template Language (DTL), which tag is used to inherit layout structure from a parent template?
- (A) `{% include 'header.html' %}`
- (B) `{% extends 'base.html' %}`
- (C) `{% block content %}`
- (D) `{% import 'base.html' %}`
**Answer:** (B) `{% extends 'base.html' %}`  
**Explanation:** `{% extends %}` tells Django that the child template builds upon a parent template layout.

#### Q12. In Django, Class-Based Views (CBVs) like `ListView` or `DetailView` are mapped in `urls.py` using which method?
- (A) `views.MyView.render()`
- (B) `views.MyView.as_view()`
- (C) `views.MyView.execute()`
- (D) `views.MyView.dispatch()`
**Answer:** (B) `views.MyView.as_view()`  
**Explanation:** `as_view()` returns a callable view function that takes a request and dispatches to appropriate HTTP methods (e.g. `get()`, `post()`).

---

## 🗄️ Unit 3: Django ORM, Models & Database Operations

#### Q13. To optimize Django ORM queries and solve the N+1 Query Problem for a `ForeignKey` relationship, which method performs a SQL `JOIN` in a single query?
- (A) `prefetch_related()`
- (B) `select_related()`
- (C) `raw()`
- (D) `aggregate()`
**Answer:** (B) `select_related()`  
**Explanation:** `select_related()` works on single-valued relationships (`ForeignKey`, `OneToOneField`) via a SQL `JOIN` in 1 query. `prefetch_related()` works on multi-valued relationships (`ManyToManyField`, reverse `ForeignKey`) using separate queries joined in Python.

#### Q14. What is the difference between Django ORM's `filter()` and `get()` methods?
- (A) `filter()` returns a single model instance; `get()` returns a QuerySet.
- (B) `filter()` returns a QuerySet containing zero, one, or multiple matching objects; `get()` returns a single model instance and raises `DoesNotExist` or `MultipleObjectsReturned` if the query doesn't yield exactly 1 match.
- (C) `get()` executes raw SQL; `filter()` does not.
- (D) `filter()` cannot accept keyword arguments.
**Answer:** (B) `filter()` returns a QuerySet containing zero, one, or multiple matching objects; `get()` returns a single model instance and raises `DoesNotExist` or `MultipleObjectsReturned` if the query doesn't yield exactly 1 match.  
**Explanation:** `filter()` always returns a list-like `QuerySet`. `get()` expects exactly one match and throws exceptions if 0 or >1 items match.

#### Q15. In a Django model `ForeignKey` field definition, what does `on_delete=models.CASCADE` specify?
- (A) Prevents deletion of the referenced parent object.
- (B) Automatically deletes child objects when the referenced parent object is deleted.
- (C) Sets the foreign key value to `NULL` upon parent deletion.
- (D) Raises a `ValidationError` when deleting.
**Answer:** (B) Automatically deletes child objects when the referenced parent object is deleted.  
**Explanation:** `CASCADE` simulates SQL cascading deletes, automatically removing all related child rows when the parent instance is deleted.

#### Q16. In Django Admin customization, which attribute in a `ModelAdmin` class specifies which columns to display in the change list view?
- (A) `search_fields`
- (B) `list_filter`
- (C) `list_display`
- (D) `ordering`
**Answer:** (C) `list_display`  
**Explanation:** `list_display` is a tuple/list of field names to display as table columns in the Django admin changelist view.

#### Q17. Which `on_delete` option in a Django `ForeignKey` prevents the parent object from being deleted if any related child objects exist?
- (A) `models.CASCADE`
- (B) `models.PROTECT`
- (C) `models.SET_NULL`
- (D) `models.DO_NOTHING`
**Answer:** (B) `models.PROTECT`  
**Explanation:** `models.PROTECT` raises `ProtectedError` (a subclass of `django.db.IntegrityError`) to prevent deletion of the parent object if child objects reference it.

---
