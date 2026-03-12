1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

SELECT  
students.\*,  
`degrees.name` AS degree

FROM `university.students`

INNER JOIN `university.degrees`  
ON `students.degree_id` = `degrees.id`

WHERE `degrees.name` = "Corso di Laurea in Economia";

2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

SELECT  
degrees.\*,  
`departments.name` AS `department_name`

FROM `university.departments`

JOIN `university.degrees`  
ON `departments.id`= `degrees.department_id`

WHERE `departments.name` = "Dipartimento di Neuroscienze"  
AND `degrees.level` = "magistrale" ;

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

SELECT  
courses.\*,
`teachers.name` as `teacher_name`,  
`teachers.surname` as `teacher_surname`

FROM `university.teachers`

JOIN `university.course_teacher`  
ON `teachers.id` = `course_teacher.teacher_id`

JOIN `university.courses`  
ON `course_teacher.course_id` = `courses.id`

WHERE `teachers.id` = "44";

4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui
   sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e
   nome

SELECT  
`students.*`,  
`degrees.*`,  
`departments.\*`

FROM `university.students`

JOIN `university.degrees`  
ON `students.degree_id` = `degrees.id`

JOIN `university.departments`  
ON `degrees.department_id` = `departments.id`  
ORDER BY `students.name`, `students.surname`;

5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

SELECT  
`degrees.*`,  
`courses.*`,  
`teachers.*`

FROM `university.degrees`

JOIN `university.courses`  
ON `degrees.id` = `courses.degree_id`

JOIN `university.course_teacher`  
ON `courses.id` = `course_teacher.course_id`

JOIN `university.teachers`  
ON `course_teacher.teacher_id` = `teachers.id`;

6. Selezionare tutti i docenti che insegnano nel Dipartimento di
   Matematica (54)

SELECT.  
`teachers.*`,  
`departments.name` AS `department_name`

FROM `university.teachers`

JOIN `university.course_teacher`  
ON `teachers.id` = `course_teacher.teacher_id`

JOIN `university.courses`  
ON `course_teacher.course_id` = `courses.id`

JOIN `university.degrees`  
ON `degrees.id` = `courses.degree_id`

JOIN `university.departments`  
ON `departments.id` = `degrees.department_id`

WHERE `departments.name` = "Dipartimento di Matematica"

GROUP BY `teachers.id`;

7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti
   per ogni esame, stampando anche il voto massimo. Successivamente,
   filtrare i tentativi con voto minimo 18.
