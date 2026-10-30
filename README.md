ABC Sr Sec School — ID Card Management System
A lightweight local school ID management application built with Flask and SQLite.
Features
Password-protected administrator dashboard
Student and staff record creation, editing, searching, deleting
Photo uploads (JPG/PNG/WEBP)
Printable ID cards with QR codes (54 × 86 mm)
Bulk print on A4, CSV import/export
Local SQLite database
Setup
Requires Python 3.10+.
python -m venv .venv
# Windows: .venv\Scripts\activate
# macOS/Linux: source .venv/bin/activate
pip install -r requirements.txt
Set an admin password (required on first run):
# Windows PowerShell
$env:ADMIN_PASSWORD="replace-with-a-strong-password"
$env:SECRET_KEY="replace-with-a-long-random-secret"
python app.py
# macOS/Linux
export ADMIN_PASSWORD='replace-with-a-strong-password'
export SECRET_KEY='replace-with-a-long-random-secret'
python app.py
Open http://127.0.0.1:5000 and sign in with username admin and your chosen password.
Set SCHOOL_NAME to override the displayed school name. DATABASE_PATH can move the database outside the project directory.
Import data
See sample_students.csv for the expected format. Each row must have a unique code, name, and role (student or staff). CSV import is transactional: a failed import does not partially save rows.
Security and deployment
For local, trusted administrator use only. Do not publish this development server on the internet. Before internet deployment add HTTPS, CSRF protection, rate limiting, hardened session cookies, backups, authorization/audit logs and appropriate data retention controls. QR codes contain the name, role and ID, so avoid distributing cards publicly. Keep the database, photos, credentials and real student records out of GitHub. Change the initial password by updating its stored hash or resetting the database before importing real data; changing ADMIN_PASSWORD after initial setup does not change an existing login. Obtain appropriate school/guardian permissions before processing children's personal information.
GitHub upload
Create a new empty repository and upload these files, or run:
git init
git add .
git commit -m "Initial school ID card manager"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
git push -u origin main
