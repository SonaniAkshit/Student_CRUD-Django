## ✅ Project: `student_crud`

A simple web app to **Create**, **Read**, **Update**, and **Delete** student records.

---

## 📁 Project Structure

```
student_crud/
│
├── manage.py
├── db.sqlite3
├── student_crud/
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   ├── wsgi.py
│
├── students/
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── models.py
│   ├── views.py
│   ├── urls.py
│   ├── forms.py
│   ├── migrations/
│   │   └── __init__.py
│
├── templates/
│   └── students/
│       ├── base.html
│       ├── student_list.html
│       ├── student_form.html
│       └── student_confirm_delete.html
```

---

<!-- ## ⚙️ Step-by-Step Instructions to Run

### ✅ Step 1: Install Django

```bash
pip install django
```

### ✅ Step 2: Create Project and App

```bash
django-admin startproject student_crud
cd student_crud
python manage.py startapp students
```

### ✅ Step 3: Add App to `settings.py`

In `student_crud/settings.py`, add `'students'` to `INSTALLED_APPS`:

```python
INSTALLED_APPS = [
    ...
    'students',
]
```

---

## 🧠 Models

**`students/models.py`**

```python
from django.db import models

class Student(models.Model):
    name = models.CharField(max_length=100)
    email = models.EmailField()
    course = models.CharField(max_length=100)
    fees = models.DecimalField(max_digits=8, decimal_places=2)

    def __str__(self):
        return self.name
```

---

## 📝 Forms

**`students/forms.py`**

```python
from django import forms
from .models import Student

class StudentForm(forms.ModelForm):
    class Meta:
        model = Student
        fields = '__all__'
```

---

## 👨‍💻 Views

**`students/views.py`**

```python
from django.shortcuts import render, redirect, get_object_or_404
from .models import Student
from .forms import StudentForm

def student_list(request):
    students = Student.objects.all()
    return render(request, 'students/student_list.html', {'students': students})

def student_create(request):
    form = StudentForm(request.POST or None)
    if form.is_valid():
        form.save()
        return redirect('student_list')
    return render(request, 'students/student_form.html', {'form': form})

def student_update(request, pk):
    student = get_object_or_404(Student, pk=pk)
    form = StudentForm(request.POST or None, instance=student)
    if form.is_valid():
        form.save()
        return redirect('student_list')
    return render(request, 'students/student_form.html', {'form': form})

def student_delete(request, pk):
    student = get_object_or_404(Student, pk=pk)
    if request.method == 'POST':
        student.delete()
        return redirect('student_list')
    return render(request, 'students/student_confirm_delete.html', {'student': student})
```

---

## 🌐 URLs

**`students/urls.py`**

```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.student_list, name='student_list'),
    path('add/', views.student_create, name='student_add'),
    path('edit/<int:pk>/', views.student_update, name='student_edit'),
    path('delete/<int:pk>/', views.student_delete, name='student_delete'),
]
```

**`student_crud/urls.py`**

```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('students.urls')),
]
```

---

## 🌍 Templates

### **base.html**

```html
<!DOCTYPE html>
<html>
<head>
    <title>Student CRUD</title>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css">
</head>
<body>
    <div class="container mt-5">
        <h2 class="mb-4">Student Management</h2>
        {% block content %}{% endblock %}
    </div>
</body>
</html>
```

### **student\_list.html**

```html
{% extends 'students/base.html' %}
{% block content %}
<a href="{% url 'student_add' %}" class="btn btn-success mb-3">Add Student</a>
<table class="table table-bordered">
    <thead>
        <tr><th>ID</th><th>Name</th><th>Email</th><th>Course</th><th>Fees</th><th>Actions</th></tr>
    </thead>
    <tbody>
        {% for student in students %}
        <tr>
            <td>{{ student.id }}</td>
            <td>{{ student.name }}</td>
            <td>{{ student.email }}</td>
            <td>{{ student.course }}</td>
            <td>{{ student.fees }}</td>
            <td>
                <a href="{% url 'student_edit' student.id %}" class="btn btn-primary btn-sm">Edit</a>
                <a href="{% url 'student_delete' student.id %}" class="btn btn-danger btn-sm">Delete</a>
            </td>
        </tr>
        {% endfor %}
    </tbody>
</table>
{% endblock %}
```

### **student\_form.html**

```html
{% extends 'students/base.html' %}
{% block content %}
<form method="post">
    {% csrf_token %}
    {{ form.as_p }}
    <button type="submit" class="btn btn-success">Save</button>
    <a href="{% url 'student_list' %}" class="btn btn-secondary">Back</a>
</form>
{% endblock %}
```

### **student\_confirm\_delete.html**

```html
{% extends 'students/base.html' %}
{% block content %}
<h4>Are you sure you want to delete {{ student.name }}?</h4>
<form method="post">
    {% csrf_token %}
    <button type="submit" class="btn btn-danger">Yes, Delete</button>
    <a href="{% url 'student_list' %}" class="btn btn-secondary">Cancel</a>
</form>
{% endblock %}
```

---

## ✅ Migrate and Run

```bash
# Inside project folder
python manage.py makemigrations
python manage.py migrate
python manage.py runserver
```

Open in browser: [http://127.0.0.1:8000](http://127.0.0.1:8000)

---

## ✅ Done!

This is a complete CRUD project using Django. -->
