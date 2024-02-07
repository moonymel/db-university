1. Selezionare tutti gli studenti nati nel 1990 (160)

SELECT *
FROM `students`
WHERE YEAR(`date_of_birth`) LIKE '1990';

2. Selezionare tutti i corsi che valgono più di 10 crediti (479)

SELECT *
FROM `courses`
WHERE `cfu` > 10;

3. Selezionare tutti gli studenti che hanno più di 30 anni

SELECT *
FROM `students`
WHERE YEAR(CURDATE()) - YEAR(`date_of_birth`) > 30;

4. Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di
laurea (286)

SELECT *
FROM `courses`
WHERE `period` = 'I semestre'
AND `year` = '1';

5. Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del
20/06/2020 (21)

SELECT *
FROM `exams`
WHERE `hour` > '13:59:59'
AND `date` = '2020-06-20';

6. Selezionare tutti i corsi di laurea magistrale (38)

SELECT *
FROM `degrees`
WHERE `level` = 'magistrale';

7. Da quanti dipartimenti è composta l'università? (12)

SELECT COUNT(*) AS `university_departments`
FROM `departments`;

8. Quanti sono gli insegnanti che non hanno un numero di telefono? (50)

SELECT *
FROM `teachers`
WHERE `phone` IS NULL;

BONUS:
Selezionare nome, descrizione e periodo di tutti i corsi che hanno sito web diverso da null, cfu compresi tra 9 e 12 e che sono del primo anno ed ordinarli in ordine decrescente

SELECT `name`, `description`, `period`
FROM `courses`
WHERE `website` IS NOT NULL
AND `cfu` BETWEEN 9 AND 12
AND `year` = 1
ORDER BY `id` DESC;