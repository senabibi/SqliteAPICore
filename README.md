# SQLiteAPICore Project

[![Contributors](https://img.shields.io/github/contributors/senabibi/SQLiteAPICore)](https://github.com/senabibi/SQLiteAPICore/graphs/contributors)
[![Forks](https://img.shields.io/github/forks/senabibi/SQLiteAPICore)](https://github.com/senabibi/SQLiteAPICore/network/members)
[![Stargazers](https://img.shields.io/github/stars/senabibi/SQLiteAPICore)](https://github.com/senabibi/SQLiteAPICore/stargazers)
[![Issues](https://img.shields.io/github/issues/senabibi/SQLiteAPICore)](https://github.com/senabibi/SQLiteAPICore/issues)
[![MIT License](https://img.shields.io/github/license/senabibi/SQLiteAPICore)](https://opensource.org/licenses/MIT)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Nursena%20Bitirgen-blue)](https://www.linkedin.com/in/nursena-bitirgen-5743341b9/)

<div align="center">
  <a href="https://github.com/senabibi/SQLiteAPICore">
    <img src="https://github.com/senabibi/SQLiteAPICore/blob/main/logo.png" alt="Logo" width="800" height="500">
  </a>
  <h3 align="center">SQLiteAPICore</h3>
  <p align="center">
    A Python-based project that demonstrates how to build a database-driven application and an API using SQLite, Django, and Django REST Framework. This project is designed to help beginners understand the fundamentals of API development, database management, and Python programming.
    <br />
    <a href="https://github.com/senabibi/SQLiteAPICore"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/senabibi/SQLiteAPICore">View Demo</a>
    ·
    <a href="https://github.com/senabibi/SQLiteAPICore/issues">Report Bug</a>
    ·
    <a href="https://github.com/senabibi/SQLiteAPICore/issues">Request Feature</a>
  </p>
</div>

---

## Table of Contents

1. [About The Project](#about-the-project)
   - [Built With](#built-with)
2. [Getting Started](#getting-started)
   - [Prerequisites](#prerequisites)
   - [Installation](#installation)
3. [Usage](#usage)
4. [Roadmap](#roadmap)
5. [Contributing](#contributing)
6. [License](#license)
7. [Contact](#contact)
8. [Acknowledgments](#acknowledgments)

---

## About The Project

The **SQLiteAPICore** project is a hands-on guide to building a database-driven application and an API using Python, SQLite, Django, and Django REST Framework. This project is designed for beginners who want to learn how to create APIs, manage databases, and develop Python applications.

The project covers the following key concepts:
- Setting up a virtual environment.
- Creating and managing SQLite databases.
- Building a Django project and app.
- Using Django REST Framework to create APIs.
- Testing APIs with Postman.

This project is a great starting point for anyone interested in backend development, API creation, and database management.

---

## Key Features

1. **Database-Driven Application**: 
   - Learn how to create and manage a SQLite database.
   - Perform CRUD (Create, Read, Update, Delete) operations using Python and Django.

2. **API Development**:
   - Build a RESTful API using Django REST Framework.
   - Create endpoints for handling data requests and responses.

3. **Testing with Postman**:
   - Use Postman to test API endpoints and ensure they work as expected.

4. **Django Integration**:
   - Set up a Django project and app.
   - Register models and create views for handling API requests.

5. **Virtual Environment**:
   - Learn how to create and activate a virtual environment for Python projects.

---

## Built With

- **Python**: The core programming language used for building the application and API.
- **SQLite**: A lightweight, serverless database management system used for storing data.
- **Django**: A high-level Python web framework used for building the project.
- **Django REST Framework**: A powerful toolkit for building Web APIs in Django.
- **Postman**: A popular tool for testing APIs.

---

## Getting Started

### Prerequisites

Before you begin, ensure you have the following installed:
- Python 3.x
- Django
- Django REST Framework
- Postman (for API testing)

### Installation

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/senabibi/SQLiteAPICore.git
   cd SQLiteAPICore
   ```
2.**Create a Virtual Environment**:
   ```bash
   python -m venv venv
source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
  ```
3.**Install Dependencies**:
   ```bash
   pip install -r requirements.txt
  ```

4.**Set Up the Database:**:
 Run the following commands to apply migrations and create the database:
   ```bash
   python manage.py makemigrations
   python manage.py migrate
  ```
5.**Create a Superuser:**:
 Create a superuser account to access the Django admin panel:
   ```bash
   python manage.py createsuperuser
  ```
6.**Run the Development Server:**:
   ```bash
   python manage.py runserver
  ```
















## Usage

<div align="center">
    <img src="https://github.com/senabibi/PostgresqlTopTen/blob/main/POST.png" alt="Post ERD">
</div>

This project demonstrates how to create a simple API using Django and Django REST Framework, which interacts with a SQLite database. It features a basic Product model with fields like name, price, and description, and provides API endpoints for performing CRUD operations.

**Steps to Set Up the Project**:

### 1. **Create a Django Project**
   - Start by creating a new Django project:
      ```bash
        django-admin startproject SQLiteAPICore
        cd SQLiteAPICore

      ```
      
### 2. **Create a Django App**
  -Create a new app within the project:
    ```bash
        python manage.py startapp api
    ```

### 3. ** Register the App**
   - Add the app to the INSTALLED_APPS list in settings.py:
    ```bash
        INSTALLED_APPS = [
    ...
    'api',
    'rest_framework',
      ]  
    ```

### 4. Create a Model**
   - Define a Product model in api/models.py:
  ```bash
        from django.db import models

class Product(models.Model):
    name = models.CharField(max_length=100)
    price = models.DecimalField(max_digits=10, decimal_places=2)
    description = models.TextField()

    def __str__(self):
        return self.name

   ```
     

### 5. Create and Apply Migrations**
   - Run the following commands to create and apply migrations for the Product model:
     ```bash
        python manage.py makemigrations
        python manage.py migrate
     ```

### 6. Create a Serializer**
   - Create a serializer for the Product model in api/serializers.py:
     ```bash
        from rest_framework import serializers
        from .models import Product

        class ProductSerializer(serializers.ModelSerializer):
        class Meta:
            model = Product
            fields = '__all__'

     ```
### 7. Create Views**
   - Create views for handling API requests in api/views.py. We will use a ModelViewSet to automatically handle CRUD operations:
     ```bash
        from rest_framework import viewsets
        from .models import Product
        from .serializers import ProductSerializer
  
        class ProductViewSet(viewsets.ModelViewSet):
          queryset = Product.objects.all()
          serializer_class = ProductSerializer

     ```
### 8.Configure URLs**
   - Map the views to URLs in api/urls.py:
     ```bash
        from django.urls import path, include
        from rest_framework.routers import Default
     ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

---


## Roadmap

- [ ] **Set Up SQLite Database:** Ensure SQLite is installed and configured properly to interact with the Django project.
- [ ] **Familiarize with Django & DRF:** Get familiar with Django framework and Django REST Framework (DRF) to understand how to interact with the API and perform database queries.
- [ ] **Database Setup:** Make sure the models are correctly defined in `models.py` and migrations are applied to create the necessary tables in SQLite.
- [ ] **CRUD Operations:** Understand the Create, Read, Update, and Delete operations that are exposed through the API endpoints.
- [ ] **Test with Postman:** Use Postman to test the API endpoints (e.g., `GET /products/`, `POST /products/`).
- [ ] **Extend the API:** Add additional features such as authentication, filtering, or sorting to the API.
- [ ] **Documentation:** Document the project and provide API documentation for users.

This roadmap outlines the key steps to understand, interact with, and test the SQLite Django project. Follow these steps to explore the capabilities of the API and work with the sales data.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

---


## Contributing

Contributions are what make the open-source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this project better, please fork the repository and create a pull request. You can also simply open an issue with the "enhancement" tag. Don't forget to give the project a star! Thanks again!

### Steps to Contribute:
1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#readme-top">back to top</a>)</p>

---

## License

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

---

## Contact

Nursena Bitirgen - [LinkedIn](https://www.linkedin.com/in/nursena-bitirgen-5743341b9/)

Project Link: [https://github.com/senabibi/SQLiteAPICore](https://github.com/senabibi/SQLiteAPICore)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

---


## Acknowledgments

The development of the SQLiteAPICore project was made possible thanks to various resources and skills:

* **Django Framework:** Special gratitude to Django for providing a robust web framework that makes developing web applications easier.
* **Django REST Framework (DRF):** Acknowledgment for DRF, which simplifies creating REST APIs in Django.
* **SQLite Database:** Appreciation for using SQLite, a lightweight and serverless database that is ideal for small to medium projects and local development.
* **Postman:** Thanks to Postman for providing an intuitive interface for testing and debugging API endpoints.
* **Open-Source Community:** Recognition for the open-source community that provides tutorials, libraries, and tools to help developers.
* **Documentation:** Gratitude for the effort put into creating clear and helpful documentation for the project, making it easier for developers to understand and contribute.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

---

