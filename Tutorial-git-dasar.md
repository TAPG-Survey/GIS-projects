# 🗂️ Panduan Git Dasar

Panduan ringkas pengoperasian Git untuk version control sehari-hari.

---

## 📦 1. Konfigurasi Awal

Lakukan sekali setelah instalasi Git.

```bash
git config --global user.name "Nama Kamu"
git config --global user.email "email@kamu.com"

# Cek konfigurasi
git config --list
```

---

## 🚀 2. Inisialisasi Repository

```bash
# Buat repo baru di folder saat ini
git init

# Clone repo yang sudah ada
git clone https://github.com/username/nama-repo.git

# Clone ke folder tertentu
git clone https://github.com/username/nama-repo.git nama-folder
```

---

## 📋 3. Melihat Status & Log

```bash
# Cek status file (modified, staged, untracked)
git status

# Lihat riwayat commit
git log

# Log ringkas satu baris
git log --oneline

# Log dengan grafik branch
git log --oneline --graph --all
```

---

## ➕ 4. Staging & Commit

```bash
# Tambahkan file tertentu ke staging area
git add nama-file.txt

# Tambahkan semua perubahan
git add .

# Tambahkan file tertentu berdasarkan pola
git add *.py

# Commit dengan pesan
git commit -m "feat: tambah fitur baru"

# Tambah dan commit sekaligus (file yang sudah tracked)
git commit -am "fix: perbaikan bug"
```

---

## 🌿 5. Branch

```bash
# Lihat semua branch
git branch

# Lihat semua branch (lokal + remote)
git branch -a

# Buat branch baru
git branch nama-branch

# Pindah ke branch lain
git checkout nama-branch

# Buat sekaligus pindah ke branch baru
git checkout -b nama-branch

# Ganti nama branch saat ini
git branch -m nama-baru

# Hapus branch (sudah di-merge)
git branch -d nama-branch

# Hapus branch paksa
git branch -D nama-branch
```

---

## 🔀 6. Merge & Rebase

```bash
# Merge branch lain ke branch saat ini
git merge nama-branch

# Merge tanpa fast-forward (buat merge commit)
git merge --no-ff nama-branch

# Rebase branch saat ini ke branch lain
git rebase nama-branch

# Batalkan rebase yang sedang berlangsung
git rebase --abort
```

---

## ☁️ 7. Remote (Push & Pull)

```bash
# Lihat remote yang terdaftar
git remote -v

# Tambahkan remote
git remote add origin https://github.com/username/repo.git

# Push ke remote
git push origin nama-branch

# Push dan set upstream (pertama kali)
git push -u origin nama-branch

# Pull perubahan dari remote
git pull origin nama-branch

# Fetch tanpa merge
git fetch origin
```

---

## ↩️ 8. Undo & Reset

```bash
# Batalkan perubahan di working directory (belum di-stage)
git checkout -- nama-file.txt

# Keluarkan file dari staging (unstage)
git reset HEAD nama-file.txt

# Undo commit terakhir, pertahankan perubahan di staging
git reset --soft HEAD~1

# Undo commit terakhir, pertahankan perubahan di working dir
git reset --mixed HEAD~1

# Undo commit terakhir, buang semua perubahan (hati-hati!)
git reset --hard HEAD~1

# Buat commit baru yang membalik commit tertentu
git revert <commit-hash>
```

---

## 🏷️ 9. Tag

```bash
# Buat tag ringan
git tag v1.0.0

# Buat tag beranotasi
git tag -a v1.0.0 -m "Rilis versi 1.0.0"

# Lihat semua tag
git tag

# Push tag ke remote
git push origin v1.0.0

# Push semua tag
git push origin --tags

# Hapus tag lokal
git tag -d v1.0.0
```

---

## 🗃️ 10. Stash (Simpan Sementara)

```bash
# Simpan perubahan sementara
git stash

# Simpan dengan label
git stash push -m "wip: fitur login"

# Lihat daftar stash
git stash list

# Ambil stash terbaru
git stash pop

# Ambil stash tertentu
git stash apply stash@{2}

# Hapus stash tertentu
git stash drop stash@{0}

# Hapus semua stash
git stash clear
```

---

## 🔍 11. Diff

```bash
# Lihat perubahan yang belum di-stage
git diff

# Lihat perubahan yang sudah di-stage
git diff --staged

# Bandingkan dua branch
git diff branch-a branch-b

# Bandingkan dua commit
git diff <hash1> <hash2>
```

---

## 🧹 12. Tips & Shortcut Berguna

```bash
# Hapus file dari tracking Git (tapi tidak dari disk)
git rm --cached nama-file.txt

# Ubah pesan commit terakhir
git commit --amend -m "pesan baru"

# Tampilkan siapa yang mengubah baris tertentu
git blame nama-file.txt

# Cari commit berdasarkan pesan
git log --grep="kata kunci"

# Lihat isi commit tertentu
git show <commit-hash>
```

---

## 📌 Alur Kerja Umum

```
1. git pull origin main          ← Selalu update dulu
2. git checkout -b fitur/xxx     ← Buat branch baru
3. [edit file]
4. git add .
5. git commit -m "feat: ..."
6. git push origin fitur/xxx     ← Push ke remote
7. Buat Pull Request di GitHub/GitLab
8. Setelah merge → git checkout main && git pull
```

---

## 🚫 File `.gitignore`

Daftar file/folder yang tidak perlu di-track Git.

```
# Contoh .gitignore
__pycache__/
*.pyc
.env
*.log
node_modules/
.DS_Store
*.shp
*.dbf
*.shx
```

---

> 💡 **Tips:** Gunakan `git status` dan `git log --oneline` sesering mungkin untuk selalu tahu posisi kamu di repository.
