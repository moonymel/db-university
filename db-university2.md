1. Contare quanti iscritti ci sono stati ogni anno

SELECT COUNT(`id`) AS `number_of_students`, YEAR(`enrolment_date`) AS `year`
FROM `students`
GROUP BY YEAR(`enrolment_date`);

2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio

SELECT COUNT(`id`) AS `number_of_teachers`, `office_address`
FROM `teachers`
GROUP BY `office_address`;

3. Calcolare la media dei voti di ogni appello d'esame

SELECT AVG(`exam_student`.`vote`) AS `average_vote`, `courses`.`name` AS `course_name` 
FROM `courses`
JOIN `exams` ON `exams`.`course_id` = `courses`.`id`
JOIN `exam_student` ON `exam_student`.`exam_id` = `exams`.`id`
GROUP BY `exams`.`course_id`;

4. Contare quanti corsi di laurea ci sono per ogni dipartimento

SELECT COUNT(`degrees`.`name`) AS `number_of_degrees`, `departments`.`name` AS `department_name`
FROM `departments`
JOIN `degrees` ON `degrees`.`department_id` = `departments`.`id`
GROUP BY `departments`.`name`;


----------


1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

SELECT `students`.*
FROM `degrees`
JOIN `students` ON `students`.`degree_id` = `degrees`.`id`
WHERE `degrees`.`name` = 'Corso di Laurea in Economia';

2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di
Neuroscienze

SELECT `degrees`.*
FROM `departments`
JOIN `degrees` ON `degrees`.`department_id` = `departments`.`id`
WHERE `degrees`.`level`= 'magistrale'
AND `departments`.`name` = 'Dipartimento di Neuroscienze';

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

SELECT `courses`.*
FROM `teachers`
JOIN `course_teacher` ON `course_teacher`.`teacher_id` = `teachers`.`id`
JOIN `courses` ON `course_teacher`.`course_id` = `courses`.`id`
WHERE `teachers`.`id` = 44;


4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui
sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e
nome

SELECT `students`.`surname` AS `student_surname`, `students`.`name` AS `student_name`, `degrees`.`name` AS `degree`, `departments`.`name` AS `department`
FROM `departments`
JOIN `degrees` ON `degrees`.`department_id` = `departments`.`id`
JOIN `students` ON `students`.`degree_id` = `degrees`.`id`
ORDER BY `students`.`surname`;


5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

SELECT

6. Selezionare tutti i docenti che insegnano nel Dipartimento di
Matematica (54)

SELECT DISTINCT `teachers`.*
FROM `departments` 
JOIN `degrees` ON `degrees`.`department_id` = `departments`.`id`
JOIN `courses` ON `courses`.`degree_id` = `degrees`.`id`
JOIN `course_teacher` ON `course_teacher`.`course_id` = `courses`.`id`
JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id`
WHERE `departments`.`name` = 'Dipartimento di Matematica';

7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti
per ogni esame, stampando anche il voto massimo. Successivamente,
filtrare i tentativi con voto minimo 18.