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