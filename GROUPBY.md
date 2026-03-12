1. Contare quanti iscritti ci sono stati ogni anno

SELECT  
COUNT(`students.id`) AS `students_number`,
YEAR(`students.enrolment_date`) AS `enrolment_year`  
FROM `university.students`  
GROUP BY YEAR(`students.enrolment_date`);

2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio

SELECT  
COUNT(`teachers.id`) AS `teachers_number`,
`teachers.office_address`  
FROM `university.teachers`  
GROUP BY `teachers.office_address` ;

3. Calcolare la media dei voti di ogni appello d'esame

SELECT  
ROUND(AVG(`exam_student.vote`)) AS `avarage_grade`,
`exam_student.exam_id`  
FROM `university.exam_student`  
GROUP BY `exam_student.exam_id`;

4. Contare quanti corsi di laurea ci sono per ogni dipartimento

SELECT  
COUNT(`degrees.name`) AS `number_of_degrees`,
`degrees.department_id`  
FROM `university.degrees`  
GROUP BY `degrees.department_id` ;
