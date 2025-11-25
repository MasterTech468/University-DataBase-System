

---

# 🎓 Academic Management Database Schema

## 📖 Overview
This project is an **Academic Management Database Schema** built with Oracle SQL.  
It models the relationships between **staff, faculties, qualifications, subjects, lectures, students, and registrations**, providing a foundation for managing academic operations in a university or college environment.

The schema demonstrates **relational database design principles** such as primary keys, foreign keys, composite keys, and referential integrity. It also includes **sample data inserts** to make testing and querying easier.

---

## 🗂️ Database Schema
The schema consists of the following tables:

| Table              | Description |
|--------------------|-------------|
| **STAFF**          | Stores staff details (ID, surname, initials, office, job, salary, bonus). |
| **FACULTY**        | Stores faculty details (code, name, head of faculty linked to staff). |
| **QUALIFICATION**  | Stores qualifications (code, name, head staff, linked to faculty). |
| **SUBJECT**        | Stores subjects (code, name, fee, head staff, qualification, prerequisite). |
| **LECTURE**        | Links subjects to lecturers (staff). |
| **STUDENT**        | Stores student details (ID, surname, initials, sex, birthdate). |
| **REGISTRATION**   | Stores student registrations for subjects, including date, campus, and final mark. |

---

## 🔗 Relationships
- **FACULTY → STAFF**: Each faculty is headed by a staff member.  
- **QUALIFICATION → FACULTY**: Each qualification belongs to a faculty.  
- **QUALIFICATION → STAFF**: Each qualification is headed by a staff member.  
- **SUBJECT → QUALIFICATION**: Each subject belongs to a qualification.  
- **SUBJECT → STAFF**: Each subject is headed by a staff member.  
- **LECTURE → SUBJECT & STAFF**: Each lecture links a subject to a lecturer.  
- **REGISTRATION → STUDENT & SUBJECT**: Students register for subjects.  

---

## ⚙️ Setup Instructions
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/academic-database.git
   ```
2. Connect to Oracle SQL*Plus or your preferred SQL client.
3. Run the schema script:
   ```sql
   @schema.sql
   ```
4. Verify tables:
   ```sql
   DESC STAFF;
   DESC STUDENT;
   DESC SUBJECT;
   ```

---

## 📥 Sample Data
The schema includes sample inserts for:
- 4 staff members (Dean, lecturers, admin staff).  
- 2 faculties (Science, Arts).  
- 2 qualifications (Computer Science, English Literature).  
- 3 subjects (Database Systems, Programming Fundamentals, Shakespeare Studies).  
- 3 students.  
- Registrations linking students to subjects with marks.  

---

## 🧪 Example Queries
```sql
-- List all students with their registered subjects and marks
SELECT s.SURNAME AS Student,
       sub.SUBJ_NAME AS Subject,
       r.FINALMARK AS Mark
FROM REGISTRATION r
JOIN STUDENT s ON r.STUDNR = s.STUDNR
JOIN SUBJECT sub ON r.SUBJ_CODE = sub.SUBJ_CODE;

-- Show which staff member is head of each faculty
SELECT f.FAC_NAME, st.SURNAME AS Head
FROM FACULTY f
JOIN STAFF st ON f.FAC_HEAD = st.STAFFNR;

-- Show lecturers assigned to subjects
SELECT sub.SUBJ_NAME, st.SURNAME AS Lecturer
FROM LECTURE l
JOIN SUBJECT sub ON l.SUBJ_CODE = sub.SUBJ_CODE
JOIN STAFF st ON l.LECTURER_NR = st.STAFFNR;
```

---

## 📊 ER Diagram

```markdown

```

---

## 📝 License
This project is licensed under the M_Tech  License  — feel free to use and adapt. (mainly for recruiters)

---

