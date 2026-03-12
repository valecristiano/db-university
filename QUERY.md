## Query

- Selezionare tutti gli studenti nati nel 1990 (160):

SELECT \*  
FROM `university.students`  
WHERE YEAR(students.date_of_birth)=1990;

- Selezionare tutti i corsi che valgono più di 10 crediti (479):

SELECT \*  
FROM `university.courses`  
WHERE `courses.cfu` > 10;

- Selezionare tutti gli studenti che hanno più di 30 anni:

SELECT \*  
FROM `university.students`  
WHERE `students.date_of_birth` < "1996-03-11";

- Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea (286):

SELECT \*  
FROM `university.courses`  
WHERE `courses.period` = "I semestre"  
AND `courses.year` = "1";

- Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020 (21):

SELECT \*  
FROM `university.exams`  
WHERE `exams.hour` > "14:00:00"  
AND `exams.date` = "2020-06-20";

- Selezionare tutti i corsi di laurea magistrale (38):

SELECT \*  
FROM `university.degrees`  
WHERE `degrees.level` = "magistrale";

- Da quanti dipartimenti è composta l'università? (12):

SELECT COUNT(departments.id)  
FROM `university.departments`;

- Quanti sono gli insegnanti che non hanno un numero di telefono? (50):

SELECT COUNT(teachers.id)  
FROM `university.teachers`  
WHERE `teachers.phone` IS NULL;
