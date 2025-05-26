Esercizio di oggi: nome repo: db-university (stessa degli altri giorni)
Dopo aver creato un nuovo database nel vostro MySQL Workbench e aver importato lo schema allegato, eseguite le query del file allegato.
Cosa consegnare?
Dopo aver testato le vostre query con MySQL Workbench, riportatele in un file txt e caricatelo nella vostra repo.

<!-- TASK 1 -->
SELECT *
FROM `students`
WHERE `date_of_birth` LIKE '1990-%';

<!-- TASK 2 -->
SELECT *
FROM `courses`
WHERE `cfu` > 10;

<!-- TASK 3 -->
SELECT *
FROM `students`
WHERE TIMESTAMPDIFF(YEAR, `date_of_birth`, CURDATE()) > 30;

<!-- TASK 4 -->
SELECT *
FROM `courses`
WHERE `period` LIKE "I semestre"
AND `year` LIKE 1;

<!-- TASK 5 -->
SELECT *
FROM `exams`
WHERE `date` LIKE "2020-06-20"
AND `hour` >= "14:00:00";

<!-- TASK 6 -->
SELECT *
FROM `degrees`
WHERE `level` LIKE "magistrale";

<!-- TASK 7 -->
SELECT COUNT(`id`) AS `total_departments`
FROM `departments`;