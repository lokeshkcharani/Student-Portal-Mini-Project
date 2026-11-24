# Student Portal Mini Project

> **4-day plan and step-by-step walkthrough for beginners: HTML, CSS and Bootstrap**

---

## 1. Project Overview

| Item | Details |
| :--- | :--- |
| **Project** | **Student Portal**: A multi-page website where a student logs in, sees a dashboard, browses courses, watches a course video, enrols through a form, and views a profile |
| **Level** | Beginner. Only HTML, CSS, and Bootstrap; no JavaScript and no backend |
| **Duration** | 4 days, about 2.5 to 3 hours per day.<br>**Daily rhythm:** Review & set up (15 min) &rarr; Build (60 min) &rarr; Break (10 min) &rarr; Build (60 min) &rarr; Test & commit (15 min) |
| **Team** | 2 trainees working as a pair: one builds, the other reviews, then they swap |
| **Data** | Sample data typed directly into the pages (names, courses, marks); buttons do not need to work yet |
| **Result** | A live website on GitHub Pages, a GitHub repository with a README, and a 5-minute demo |
| **Reference images** | A design canvas with a mockup of every page: [View Mockups](https://claude.ai/artifact/KNmDz3XnQiBeGGJL8cbU1e) |

### What You Will Practise

| Topic | Where it appears |
| :--- | :--- |
| **HTML structure and semantic tags** | Every page: `<header>`, `<nav>`, `<main>`, `<section>`, `<footer>` |
| **Multimedia: video, audio, iframe** | Course detail page (`course-detail.html`) |
| **CSS types and selectors** | Bootstrap link plus external `style.css` with class, descendant, and hover selectors |
| **Box model** | Cards, spacing, borders, shadows |
| **Flexbox and Grid** | A hand-written Flexbox row and a CSS Grid layout in `style.css`, plus Bootstrap's grid |
| **Forms** | Login, Register, and Enrol pages |
| **Bootstrap** | Navbar, grid, cards, table, list group, accordion, form classes, modal, collapse |
| **Git and GitHub** | Branches, commits, pull requests, README, GitHub Pages |

### The Pages

| Page | Contents |
| :--- | :--- |
| `index.html` (Login) | Centred card with email, password, remember me, Login button, link to Register |
| `register.html` | Card with name, email, phone, password, confirm password, terms checkbox |
| `dashboard.html` | Welcome line, 4 stat cards, today's classes table, notice board |
| `courses.html` | Filter buttons and 6 course cards in a grid |
| `course-detail.html` | Lecture video, audio introduction, map iframe, syllabus accordion, Enrol button |
| `enrol.html` | Enrolment form with all form controls and a confirmation modal |
| `profile.html` | Student details, weekly timetable table, marks and attendance table |

---

## 2. Before You Start

### Tools Checklist
- [ ] VS Code with the **Live Server** extension, Chrome, and Git installed
- [ ] GitHub account for each trainee
- [ ] A few free images (course pictures, profile photo) saved in an `assets/images/` folder (use your own photos or sites like [Unsplash](https://unsplash.com) or [Pexels](https://pexels.com))
- [ ] One short sample video (`.mp4`) and one short audio file (`.mp3`), 30 to 60 seconds each (you can record your own on a phone)

### Folder Structure
```text
student-portal/
  index.html            (login page)
  register.html
  dashboard.html
  courses.html
  course-detail.html
  enrol.html
  profile.html
  css/
    style.css
  assets/
    images/
    video/
    audio/
  README.md
```

> **Naming rule:** Use lowercase names with hyphens and no spaces. GitHub Pages is case-sensitive: `Photo.jpg` and `photo.jpg` are different files, and case mismatches are the #1 reason images fail to load online.

### Base Template for Every Page
Copy this skeleton into each new page and change the `<title>`. It loads Bootstrap first and your own `style.css` second, allowing your rules to override Bootstrap defaults.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Student Portal | Dashboard</title>
  <link rel="stylesheet"
    href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css">
  <link rel="stylesheet" href="css/style.css">
</head>
<body>
 
  <!-- page content here -->
 
  <script
    src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>
```

### Starter `style.css`
```css
:root {
  --brand: #2f5fd0;
  --brand-dark: #244aa3;
  --bg: #f4f6fb;
  --ink: #1d2433;
}

* { 
  box-sizing: border-box; 
}

body {
  background-color: var(--bg);
  color: var(--ink);
  font-family: "Poppins", Arial, sans-serif;
}

.bg-brand { 
  background-color: var(--brand) !important; 
}

.btn-brand {
  background-color: var(--brand);
  color: #fff;
}

.btn-brand:hover { 
  background-color: var(--brand-dark); 
  color: #fff; 
}
```

### Working as a Pair
| Role | What to do |
| :--- | :--- |
| **Builder** | Writes the page; types the code (no copy-pasting from other pages without understanding it) |
| **Reviewer** | Reads the code, checks the page against the mockup and the checklist, writes one improvement comment on GitHub |
| **Swap** | After every page, swap roles! |

---

## 3. Four-Day Timeline at a Glance

| Day | Focus | Pages | Git |
| :---: | :--- | :--- | :--- |
| **1** | Setup, layout, login and register | `index.html`, `register.html`, `dashboard.html` skeleton (navbar & sidebar) | Repo, first branch, first push |
| **2** | Dashboard, courses, profile | `dashboard.html`, `courses.html`, `profile.html` | Feature branches and merge |
| **3** | Multimedia and forms | `course-detail.html`, `enrol.html` with modal | Pull request and review |
| **4** | Responsive, polish, publish | All pages, README, deployment, demo | Merge, GitHub Pages |

---

## Day 1: Setup, Layout, Login and Register

### Goals
- Create the GitHub repository and the project structure
- Plan the pages on paper
- Build the login and register pages with Bootstrap forms
- Build the shared layout (navbar and sidebar) on the dashboard page

### Walkthrough

#### Step 1: Repository and structure (20 minutes)
1. One trainee creates a public repository on GitHub named `student-portal` with a README and adds the other as a collaborator (**Settings** &rarr; **Collaborators**).
2. Both clone it:
   ```bash
   git clone https://github.com/username/student-portal.git
   ```
3. Open the folder in VS Code and create the folders and empty files according to the structure in Section 2.
4. Commit and push:
   ```bash
   git add .
   git commit -m "Add project structure"
   git push
   ```

#### Step 2: Sketch the pages (15 minutes)
On paper, draw a box layout of each page using the mockups as reference. Mark where the navbar, sidebar, cards, table, and form go. This makes coding much faster!

#### Step 3: Login page, `index.html` (40 minutes)
1. Create a branch first:
   ```bash
   git switch -c feature-login
   ```
2. Use the base template and place the following inside `<body>`:

```html
<main class="d-flex align-items-center justify-content-center min-vh-100 p-3">
  <div class="card shadow-sm" style="width: 100%; max-width: 380px;">
    <div class="card-body p-4">
      <h1 class="h4 text-center mb-1">Student Portal</h1>
      <p class="text-center text-muted">Login to your account</p>
      <form>
        <div class="mb-3">
          <label for="email" class="form-label">Email</label>
          <input type="email" class="form-control" id="email"
                 placeholder="name@example.com" required>
        </div>
        <div class="mb-3">
          <label for="password" class="form-label">Password</label>
          <input type="password" class="form-control" id="password" required>
        </div>
        <div class="form-check mb-3">
          <input class="form-check-input" type="checkbox" id="remember">
          <label class="form-check-label" for="remember">Remember me</label>
        </div>
        <a href="dashboard.html" class="btn btn-brand w-100">Login</a>
      </form>
      <p class="text-center mt-3 mb-0">New student? <a href="register.html">Register</a></p>
    </div>
  </div>
</main>
```
- `min-vh-100` makes the area full viewport height; `d-flex` with `align-items-center` and `justify-content-center` centres the card.
- The **Login** button is an `<a>` link for now so you can navigate between pages.
- `required` adds standard browser validation.

#### Step 4: Register page, `register.html` (30 minutes)
Build it the same way. Use the same card container, with these fields in order, each wrapped in a `div` with class `mb-3` containing a `label` and an `input` with class `form-control`:

| Label | Input type | Notes |
| :--- | :--- | :--- |
| Full name | `text` | `placeholder="Student Name"` |
| Email | `email` | `required` |
| Phone | `tel` | `placeholder="Phone number"` |
| Password | `password` | `required`, `minlength="8"` |
| Confirm password | `password` | `required` |
| I agree to the terms | `checkbox` | use `form-check` classes |

Add a Register button (`btn btn-brand w-100`) and a link back to `index.html`. Commit:
```bash
git add .
git commit -m "Add login and register pages"
```

#### Step 5: Dashboard layout, `dashboard.html` (45 minutes)
Switch branch:
```bash
git switch main
git merge feature-login
git switch -c feature-layout
```
This layout will be reused on every inner page:

```html
<nav class="navbar navbar-expand-lg navbar-dark bg-brand">
  <div class="container-fluid">
    <a class="navbar-brand" href="dashboard.html">Student Portal</a>
    <button class="navbar-toggler" type="button"
            data-bs-toggle="collapse" data-bs-target="#topNav">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="topNav">
      <ul class="navbar-nav ms-auto">
        <li class="nav-item"><a class="nav-link" href="courses.html">Courses</a></li>
        <li class="nav-item"><a class="nav-link" href="enrol.html">Enrol</a></li>
        <li class="nav-item"><a class="nav-link" href="profile.html">Profile</a></li>
        <li class="nav-item"><a class="nav-link" href="index.html">Logout</a></li>
      </ul>
    </div>
  </div>
</nav>
 
<div class="container-fluid">
  <div class="row">
    <aside class="col-md-2 bg-white border-end min-vh-100 p-3">
      <nav class="nav flex-column">
        <a class="nav-link active" href="dashboard.html">Dashboard</a>
        <a class="nav-link" href="courses.html">Courses</a>
        <a class="nav-link" href="enrol.html">Enrol</a>
        <a class="nav-link" href="profile.html">Profile</a>
      </nav>
    </aside>
    <main class="col-md-10 p-4">
      <h1 class="h3">Welcome back, Student Name</h1>
      <!-- Day 2: dashboard content goes here -->
    </main>
  </div>
</div>
```
- The row has 12 columns: the sidebar occupies 2 and the main area occupies 10.
- On phones the sidebar is wide because `col-md-2` only applies from tablet size upwards; this is refined on Day 4.
- The same navbar and sidebar HTML is reused across the other inner pages; only the `.active` link changes.

### Day 1 End of Day
1. Open every page in the browser and test all links.
2. Commit and push the branch:
   ```bash
   git push -u origin feature-layout
   ```
3. On GitHub, open a pull request, ask your partner to review it, then merge it into `main`.
4. Both run:
   ```bash
   git switch main
   git pull
   ```

### Day 1 Checklist
- [ ] Repository created, both trainees can push, project structure committed
- [ ] Login page matches the mockup and links to dashboard and register pages
- [ ] Register page has all six fields and a link back to login
- [ ] Dashboard has the navbar and sidebar layout with working links
- [ ] At least 4 meaningful commits and one merged pull request

### Check Questions
- What does the Bootstrap class `card` do, and what does `mb-3` do?
- Why must the Bootstrap `<link>` come before your own `style.css`?
- How many columns does the Bootstrap grid have, and what does `col-md-2` mean?

---

## Day 2: Dashboard, Courses and Profile

### Goals
- Fill the dashboard with stat cards, a classes table, and a notice board
- Build the courses page with a grid of cards
- Build the profile page with tables
- Write your own Flexbox and Grid CSS in `style.css`

### Walkthrough

#### Step 1: Dashboard stat cards (30 minutes)
Create a branch:
```bash
git switch -c feature-dashboard
```
Replace the comment in `<main>` with a CSS Grid of four stat cards:

```html
<div class="stat-grid mb-4">
  <div class="card stat-card"><div class="card-body">
    <p class="text-muted mb-1">Enrolled courses</p><p class="display-6 mb-0">5</p>
  </div></div>
  <div class="card stat-card"><div class="card-body">
    <p class="text-muted mb-1">Attendance</p><p class="display-6 mb-0">92%</p>
  </div></div>
  <div class="card stat-card"><div class="card-body">
    <p class="text-muted mb-1">Assignments due</p><p class="display-6 mb-0">3</p>
  </div></div>
  <div class="card stat-card"><div class="card-body">
    <p class="text-muted mb-1">Upcoming exams</p><p class="display-6 mb-0">2</p>
  </div></div>
</div>
```

Add to `css/style.css`:
```css
.stat-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 16px;
}

.stat-card {
  border: 0;
  border-left: 4px solid var(--brand);
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
}
```

#### Step 2: Today's classes and notice board (30 minutes)
```html
<div class="row g-3">
  <div class="col-lg-7">
    <div class="card"><div class="card-body">
      <h2 class="h5">Today's classes</h2>
      <table class="table table-striped mb-0">
        <thead><tr><th>Time</th><th>Course</th><th>Room</th></tr></thead>
        <tbody>
          <tr><td>9:00</td><td>HTML and CSS Basics</td><td>101</td></tr>
          <tr><td>11:00</td><td>Python Basics</td><td>Lab 2</td></tr>
          <tr><td>2:00</td><td>Communication Skills</td><td>204</td></tr>
        </tbody>
      </table>
    </div></div>
  </div>
  <div class="col-lg-5">
    <div class="card"><div class="card-body">
      <h2 class="h5">Notice board</h2>
      <ul class="list-group list-group-flush">
        <li class="list-group-item">Assignment 2 due on Friday</li>
        <li class="list-group-item">Library closed on Saturday</li>
        <li class="list-group-item">Mid-term timetable published</li>
      </ul>
    </div></div>
  </div>
</div>
```
Commit:
```bash
git add .
git commit -m "Add dashboard content"
```
Merge into `main` when the page matches the mockup.

#### Step 3: Courses page (45 minutes)
New branch:
```bash
git switch -c feature-courses
```
Copy navbar and sidebar from dashboard (set active link to **Courses**). In `<main>`:

```html
<h1 class="h3 mb-3">Courses</h1>
 
<div class="btn-group mb-4" role="group" aria-label="Course filters">
  <button type="button" class="btn btn-brand">All</button>
  <button type="button" class="btn btn-outline-primary">Web</button>
  <button type="button" class="btn btn-outline-primary">Programming</button>
  <button type="button" class="btn btn-outline-primary">Soft skills</button>
</div>
 
<div class="row row-cols-1 row-cols-md-2 row-cols-xl-3 g-4">
  <div class="col">
    <div class="card course-card h-100">
      <img src="assets/images/html-css.jpg" class="card-img-top" alt="HTML and CSS course">
      <div class="card-body">
        <h2 class="h5 card-title">HTML and CSS Basics</h2>
        <p class="card-text text-muted">6 weeks <span class="badge text-bg-primary">Beginner</span></p>
      </div>
      <div class="card-footer course-footer">
        <span>Instructor: Name</span>
        <a href="course-detail.html" class="btn btn-brand btn-sm">View</a>
      </div>
    </div>
  </div>
  <!-- Repeat the col block for 5 more courses -->
</div>
```

Add this Flexbox rule and hover effect to `css/style.css`:
```css
.course-footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.course-card {
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.course-card:hover {
  transform: translateY(-6px);
  box-shadow: 0 10px 24px rgba(0, 0, 0, 0.18);
}

.course-card .card-img-top {
  height: 160px;
  object-fit: cover;
}
```
- `row-cols-1 row-cols-md-2 row-cols-xl-3` creates 1 column on phones, 2 on tablets, and 3 on desktops.
- `h-100` ensures all cards in a row have identical height.
- Use these 6 courses: *HTML and CSS Basics*, *Python Basics*, *Java Fundamentals*, *Database Basics*, *Data Structures*, *Communication Skills*.

#### Step 4: Profile page (40 minutes)
New branch:
```bash
git switch -c feature-profile
```
In `<main>`:

```html
<h1 class="h3 mb-3">My profile</h1>
 
<div class="card mb-4"><div class="card-body d-flex align-items-center gap-3 flex-wrap">
  <img src="assets/images/student.jpg" alt="Student photo"
       class="rounded-circle" width="96" height="96" style="object-fit: cover;">
  <div>
    <h2 class="h5 mb-1">Student Name</h2>
    <p class="text-muted mb-0">ID: STU-001 | name@example.com | Phone number</p>
  </div>
</div></div>
 
<div class="row g-3">
  <div class="col-lg-6">
    <div class="card"><div class="card-body">
      <h2 class="h5">Weekly timetable</h2>
      <table class="table table-bordered mb-0">
        <thead><tr><th>Day</th><th>9:00</th><th>11:00</th><th>2:00</th></tr></thead>
        <tbody>
          <tr><td>Mon</td><td>HTML</td><td>Python</td><td>Free</td></tr>
          <!-- Add Tue to Fri -->
        </tbody>
      </table>
    </div></div>
  </div>
  <div class="col-lg-6">
    <div class="card"><div class="card-body">
      <h2 class="h5">Marks and attendance</h2>
      <table class="table table-bordered mb-0">
        <thead><tr><th>Subject</th><th>Marks</th><th>Attendance</th></tr></thead>
        <tbody>
          <tr><td>HTML and CSS Basics</td><td>78 / 100</td><td>95%</td></tr>
          <!-- Add 2 more subjects -->
        </tbody>
      </table>
    </div></div>
  </div>
</div>
```

### Day 2 End of Day
1. Check every page against its mockup side by side.
2. Merge each feature branch through a pull request and review your partner's code.
3. Run `git pull` on `main` so both teammates stay in sync.

### Day 2 Checklist
- [ ] Dashboard: 4 stat cards in a CSS Grid, classes table, notice board
- [ ] Courses: filter buttons and 6 cards that look the same height, with a hover effect
- [ ] Profile: round photo, details, timetable table, and marks table
- [ ] `style.css` contains at least one Flexbox rule, one Grid rule, one hover effect, and one box-shadow
- [ ] All three pages use the same navbar and sidebar with the correct active link
- [ ] At least 6 more commits and merged pull requests

### Check Questions
- What is the difference between Bootstrap's `row`/`col` and your own CSS Grid?
- What does `h-100` do on a card?
- Why is the transition written on `.course-card` and not only on `:hover`?

---

## Day 3: Multimedia and Forms

### Goals
- Build the course detail page using video, audio, and iframe
- Build a syllabus accordion
- Build the enrolment form with every form control and a confirmation modal

### Walkthrough

#### Step 1: Prepare your media (15 minutes)
- Place a short `.mp4` video in `assets/video/` and an `.mp3` in `assets/audio/` (under 20 MB each is best).
- **Map:** Open Google Maps &rarr; search a place &rarr; click **Share** &rarr; choose **Embed a map** &rarr; copy the `<iframe>` tag.
- If using hosted video: On YouTube click **Share** &rarr; **Embed** &rarr; copy the iframe code.

#### Step 2: Course detail page (60 minutes)
Branch:
```bash
git switch -c feature-course-detail
```
Copy navbar and sidebar. In `<main>`:

```html
<h1 class="h3 mb-3">HTML and CSS Basics</h1>
 
<div class="row g-4">
  <div class="col-lg-7">
    <div class="ratio ratio-16x9 mb-3">
      <video controls poster="assets/images/html-css.jpg">
        <source src="assets/video/lecture.mp4" type="video/mp4">
        Your browser does not support the video tag.
      </video>
    </div>
 
    <div class="card mb-3"><div class="card-body">
      <h2 class="h6">Instructor introduction (audio)</h2>
      <audio controls class="w-100">
        <source src="assets/audio/intro.mp3" type="audio/mpeg">
        Your browser does not support the audio tag.
      </audio>
    </div></div>
 
    <h2 class="h6">Campus location</h2>
    <iframe src="PASTE-THE-EMBED-LINK-HERE" width="100%" height="250"
            style="border: 0;" loading="lazy" title="Campus map"></iframe>
  </div>
 
  <div class="col-lg-5">
    <div class="card mb-3"><div class="card-body">
      <h2 class="h5">Syllabus</h2>
      <div class="accordion" id="syllabus">
        <div class="accordion-item">
          <h3 class="accordion-header">
            <button class="accordion-button" type="button"
                    data-bs-toggle="collapse" data-bs-target="#w1">
              Week 1: Web basics
            </button>
          </h3>
          <div id="w1" class="accordion-collapse collapse show" data-bs-parent="#syllabus">
            <div class="accordion-body">How the web works, VS Code, first page.</div>
          </div>
        </div>
        <!-- Add Week 2 (HTML), Week 3 (CSS), Week 4 (Bootstrap) the same way
             with new ids: w2, w3, w4 -->
      </div>
    </div></div>
    <div class="card"><div class="card-body">
      <p class="text-muted">6 weeks | Beginner | Instructor: Name</p>
      <a href="enrol.html" class="btn btn-brand">Enrol now</a>
    </div></div>
  </div>
</div>
```
- `ratio ratio-16x9` keeps the video responsive in a 16:9 aspect ratio.
- `controls` provides standard play, pause, and volume controls.
- The text inside `<video>` and `<audio>` serves as a fallback for older browsers.
- `title` on the `<iframe>` ensures accessibility for screen readers.
- In the accordion, each item requires a unique `id` and a matching `data-bs-target`.

#### Step 3: Enrol form (50 minutes)
Branch:
```bash
git switch -c feature-enrol
```
In `<main>`:

```html
<h1 class="h3 mb-3">Course enrolment</h1>
 
<form class="card card-body">
  <div class="row g-3">
    <div class="col-md-6">
      <label for="fullname" class="form-label">Full name</label>
      <input type="text" class="form-control" id="fullname" required>
    </div>
    <div class="col-md-6">
      <label for="email" class="form-label">Email</label>
      <input type="email" class="form-control" id="email" required>
    </div>
    <div class="col-md-6">
      <label for="dob" class="form-label">Date of birth</label>
      <input type="date" class="form-control" id="dob">
    </div>
    <div class="col-md-6">
      <label for="course" class="form-label">Course</label>
      <select class="form-select" id="course">
        <option selected>Choose a course</option>
        <option>HTML and CSS Basics</option>
        <option>Python Basics</option>
      </select>
    </div>
 
    <div class="col-md-6">
      <p class="mb-2">Gender</p>
      <div class="form-check form-check-inline">
        <input class="form-check-input" type="radio" name="gender" id="g1">
        <label class="form-check-label" for="g1">Female</label>
      </div>
      <div class="form-check form-check-inline">
        <input class="form-check-input" type="radio" name="gender" id="g2">
        <label class="form-check-label" for="g2">Male</label>
      </div>
    </div>
    <div class="col-md-6">
      <p class="mb-2">Interests</p>
      <div class="form-check form-check-inline">
        <input class="form-check-input" type="checkbox" id="i1">
        <label class="form-check-label" for="i1">Web</label>
      </div>
      <div class="form-check form-check-inline">
        <input class="form-check-input" type="checkbox" id="i2">
        <label class="form-check-label" for="i2">Data</label>
      </div>
    </div>
 
    <div class="col-12">
      <label for="address" class="form-label">Address</label>
      <textarea class="form-control" id="address" rows="3"></textarea>
    </div>
    <div class="col-12">
      <label for="photo" class="form-label">Photo</label>
      <input type="file" class="form-control" id="photo">
    </div>
    <div class="col-12">
      <div class="form-check">
        <input class="form-check-input" type="checkbox" id="terms" required>
        <label class="form-check-label" for="terms">I agree to the terms</label>
      </div>
    </div>
    <div class="col-12">
      <button type="button" class="btn btn-brand"
              data-bs-toggle="modal" data-bs-target="#confirmModal">Submit</button>
    </div>
  </div>
</form>
```

#### Step 4: Confirmation modal (20 minutes)
Add this directly after the `<form>`, before the closing `</main>` tag:

```html
<div class="modal fade" id="confirmModal" tabindex="-1" aria-hidden="true">
  <div class="modal-dialog modal-dialog-centered">
    <div class="modal-content">
      <div class="modal-header">
        <h2 class="modal-title h5">Confirm enrolment</h2>
        <button type="button" class="btn-close" data-bs-dismiss="modal"
                aria-label="Close"></button>
      </div>
      <div class="modal-body">Are you sure you want to enrol in this course?</div>
      <div class="modal-footer">
        <button type="button" class="btn btn-outline-secondary"
                data-bs-dismiss="modal">Cancel</button>
        <a href="dashboard.html" class="btn btn-brand">Confirm</a>
      </div>
    </div>
  </div>
</div>
```

### Day 3 End of Day
1. Test video, audio, and map; open in DevTools device mode.
2. Click **Submit** with empty required fields and check browser validation messages.
3. Open pull requests, review each other's code, and merge.
4. Run `git pull` on `main`.

### Day 3 Checklist
- [ ] Video plays with controls and poster image; audio plays; map renders properly
- [ ] Accordion opens and closes; each item has a unique id
- [ ] Enrol form includes text, email, date, select, radio, checkbox, textarea, file input, and terms
- [ ] Every input has a label connected with `for` and `id`; required fields are marked
- [ ] Modal opens from Submit and closes with Cancel; Confirm routes to dashboard
- [ ] Course buttons on courses page link to detail page

### Check Questions
- What is the difference between `<video>`, `<audio>`, and `<iframe>` elements?
- Why do all radio buttons in a group share the same `name` attribute?
- What does `data-bs-toggle="modal"` do?

---

## Day 4: Responsive, Polish and Publish

### Goals
- Make every page responsive on phone, tablet, and desktop
- Ensure visual and design consistency
- Write the final README and deploy to GitHub Pages
- Present the project in a 5-minute demo

### Walkthrough

#### Step 1: Responsive sidebar (40 minutes)
Branch:
```bash
git switch -c feature-responsive
```
On phones, collapse the sidebar behind a Menu toggle button. On every inner page, update the `<aside>` and wrap inside the layout row:

```html
<div class="container-fluid">
  <div class="row">
    <div class="col-12 d-md-none p-3 pb-0">
      <button class="btn btn-outline-primary" type="button"
              data-bs-toggle="collapse" data-bs-target="#sideMenu">Menu</button>
    </div>
    <aside class="col-md-2 bg-white border-end p-3 collapse d-md-block" id="sideMenu">
      <nav class="nav flex-column">
        <a class="nav-link active" href="dashboard.html">Dashboard</a>
        <a class="nav-link" href="courses.html">Courses</a>
        <a class="nav-link" href="enrol.html">Enrol</a>
        <a class="nav-link" href="profile.html">Profile</a>
      </nav>
    </aside>
    <main class="col-md-10 p-4"> ... </main>
  </div>
</div>
```
- `collapse` hides the sidebar on small screens; `d-md-block` displays it as a block from medium screens (`>=768px`) upwards.
- `d-md-none` displays the toggle button on phones only.
- Remove `min-vh-100` from the `<aside>` if it causes unwanted stretching on mobile.

#### Step 2: Media queries and flexible media (20 minutes)
Add to `css/style.css`:
```css
img, video, iframe {
  max-width: 100%;
}

@media (max-width: 576px) {
  .display-6 { 
    font-size: 1.8rem; 
  }
  main { 
    padding: 16px !important; 
  }
  .course-footer { 
    flex-direction: column; 
    gap: 8px; 
    align-items: flex-start; 
  }
}
```

#### Step 3: Test and fix (30 minutes)
1. Open each page in Chrome, press `F12` and toggle Device Toolbar (`Ctrl+Shift+M`).
2. Test viewports: 390px (mobile), 768px (tablet), 1280px (desktop).
3. Fix overflow issues, awkward overlaps, or spacing glitches.
4. Verify all hyperlinks, form buttons, and asset paths (lowercase names).

#### Step 4: Polish (20 minutes)
- Maintain 2–3 consistent brand colours, uniform typography, and regular spacing across all pages.
- Ensure hover effects on buttons and cards feel natural.
- Add a footer with copyright/project details on every page.
- Ensure every image has descriptive `alt` text and every page has a distinct `<title>`.

#### Step 5: README (15 minutes)
Create a clear `README.md` at root:
```markdown
# Student Portal

A beginner mini project built with HTML, CSS and Bootstrap during frontend training.

## Pages
- Login and Register
- Dashboard
- Courses and Course Detail (video, audio, map)
- Enrolment form
- Profile

## Built with
HTML5, CSS3 (Flexbox and Grid), Bootstrap 5

## Team
Names of both trainees

## Live site
[Open the Student Portal](https://username.github.io/student-portal/)

## What I learned
Write 3 to 4 lines.
```

#### Step 6: Publish on GitHub Pages (15 minutes)
1. Merge `feature-responsive` into `main` via PR and pull locally.
2. In your GitHub repo: **Settings** &rarr; **Pages**.
3. Under **Build and deployment**, select **Deploy from a branch**, Branch: `main`, Folder: `/ (root)`, and click **Save**.
4. Allow 1–2 minutes for deployment, visit the live URL, test all pages, and verify assets.
5. Add the live URL to your README.

#### Step 7: Demo (5 minutes per team)
| No. | What to show |
| :---: | :--- |
| **1** | The live site: login &rarr; dashboard &rarr; courses &rarr; course detail &rarr; enrolment form &rarr; profile |
| **2** | Responsive layout in mobile view showing the collapsible sidebar menu |
| **3** | Highlight custom CSS (Flexbox or Grid) and explain how it works |
| **4** | GitHub commit history and merged pull requests |
| **5** | Share one key challenge faced and how it was resolved |

### Final Project Checklist
- [ ] All 7 pages exist and are linked; navigation works both ways
- [ ] Semantic HTML tags used with a single `<h1>` per page
- [ ] Bootstrap utilized for navbar, grid, cards, tables, forms, accordion, and modal
- [ ] Custom `style.css` includes CSS variables, Flexbox, Grid, hover effects, and box-shadow
- [ ] Video, audio, and map iframe functional on course detail page
- [ ] Responsive across mobile, tablet, and desktop viewports
- [ ] At least 15 commits from both trainees, with feature branches and pull requests
- [ ] Deployed live on GitHub Pages with link added to README

---

## 4. Evaluation Rubric

Score each area from 1 (*Needs Work*) to 5 (*Excellent*):

| Area | Trainee 1 | Trainee 2 | Notes |
| :--- | :---: | :---: | :--- |
| HTML structure and semantic tags | | | |
| Bootstrap components and grid | | | |
| Custom CSS (Flexbox, Grid, box model) | | | |
| Multimedia (video, audio, iframe) | | | |
| Forms and labels | | | |
| Responsive design | | | |
| Git & GitHub (commits, branches, PRs) | | | |
| README and deployment | | | |
| Demo and explanation | | | |

---

## 5. Troubleshooting

| Problem | Fix |
| :--- | :--- |
| **Bootstrap styles do not appear** | Check the `<link>` tag spelling, CDN URL, and internet connection. Ensure it is placed inside `<head>`. |
| **Navbar toggle, accordion or modal does not work** | Ensure Bootstrap JS bundle script is added right before `</body>`. Verify matching `id` and `data-bs-target`. |
| **Custom CSS does not override Bootstrap** | Ensure `style.css` is linked **after** Bootstrap, or use more specific selectors. |
| **Video does not play** | Use standard MP4 (H.264); check file paths and avoid large file sizes. |
| **Map iframe is blank** | Use the **Embed a map** iframe URL from Google Maps, not standard search URL. |
| **Images missing on GitHub Pages** | File paths are case-sensitive online. Ensure filename casing and paths match exactly. |
| **Page 404 on GitHub Pages** | Verify `index.html` resides in the root folder of the repository. |
| **Merge conflict** | Open the conflicting file, retain the desired lines, remove conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`), then `git add` and `git commit`. |
| **Sidebar does not hide on phone** | Verify `collapse` and `d-md-block` classes on `<aside>` and matching `data-bs-target` on the Menu button. |

---

## 6. Stretch Ideas
- [ ] **Dark Theme:** Add a theme switcher using CSS custom properties (variables)
- [ ] **Course Search & Sort:** Add a visual search bar and sorting dropdown to the courses page
- [ ] **Printable Timetable:** Implement `@media print` styles for clean printing of the profile timetable
- [ ] **FAQ / Help Page:** Create a contact page featuring an accordion for FAQs
- [ ] **Footer:** Build a unified global footer with social links and contact info
#   S t u d e n t - P o r t a l - M i n i - P r o j e c t  
 