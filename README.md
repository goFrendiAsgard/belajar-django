# Tahapan mencoba git

```bash
# membuat satu folder
mkdir belajar-django

# masuk ke folder tersebut
cd belajar-django

# menginisiasi git repo di folder tersebut
git init

# membuat file README.md
echo "helo" > README.md

# cek status
git status # file README sudah ada, tapi belum ter track

# tambahkan file supaya ter track
git add . -A
# git add README.md

# cek status
git status # file README sudah ter track, tapi belum ter commit

# commit
git commit -m "komit pertama saya"

# cek status
git status # file README sudah ter-commit (ada pesan nothing to commit)

# tambahkan origin yang mengarah ke github
git remote add origin git@github.com:goFrendiAsgard/belajar-django.git # sesuaikan repo nya

# push semua commit yang kita lakukan di local ke github
git push -u origin main
```

# Menggunakan environment variable

- Buat `.gitignore`, tambahkan `dev.env` dan `prod.env` ke dalam `.gitignore`

- Isi `prod.env` dan `dev.env` dengan environment prod dan dev

    ```bash
    export CONNECTION_STRING=pymysql://dev@localhost:3306
    ```

- Load konfigurasi dari `.env`.
    - Jika menggunakan python, bisa memanfaatkan `os.getenv('NAMA_ENV_VARIABLE')`

- Jalankan program dengan cara me-load env yang dikehendaki

    ```bash
    # load env dev
    source dev.env
    python load-env-sample.py

    # load env prod
    source prod.env
    python load-env-sample.py
    ```

# Membuat virtual environment

```bash
python -m venv venv
```

# Mengaktifkan virtual environment

```bash
source venv/bin/activate
```

# Install django

```bash
pip install django
```

# Bikin project

```bash
django-admin startproject myweb
```

# Bikin app

```bash
cd myweb
# location: myweb
django-admin startapp polls
```

# Jalankan web

```bash
# location: myweb
python manage.py runserver
```

# Jalankan migration

```bash
# location: myweb
python manage.py migrate
```

# Register app ke project

```python
# location: myweb/settings.py

INSTALLED_APPS = [
    'polls.apps.PollsConfig', # tambahkan baris ini
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]    
```

# Ikuti tutorial

[tutorial django](https://docs.djangoproject.com/en/4.1/intro/tutorial02/)

## Bikin model

```python
# location: myweb/polls/models.py
from django.db import models

class Question(models.Model):
    question_text = models.CharField(max_length=200)
    pub_date = models.DateTimeField('date published')


class Choice(models.Model):
    question = models.ForeignKey(Question, on_delete=models.CASCADE)
    choice_text = models.CharField(max_length=200)
    votes = models.IntegerField(default=0)
```

## Buat migration

```python
python manage.py makemigrations
```

## Jalankan migration

```
python manage.py migrate
```

## Eksplorasi ORM

[contoh shell api](https://github.com/goFrendiAsgard/django-asia#accessing-api-shell)

# Glossary

> __Note:__ Ini bukan definisi resmi

- scaffolding: Proses membuat boilerplate aplikasi menggunakan tools seperti `django-admin` atau `artisan`.
- boilerplate: Template aplikasi awal yang bisa kita modif sesuai kebutuhan.
- package manager: tools untuk menginstall paket-paket/library tambahan, contoh
    - npm: node package manager (punya Node.js)
    - composer: punya PHP
    - cargo: rust
    - pip: python
    - gem: ruby
- migration: proses membuat/update schema database menggunakan tool (misalnya dengan perintah `python manage.py migrate`)
- orm: object relational mapping