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

<!-- TASK 8 -->
SELECT COUNT(*) AS `teachers_without_number`
FROM `teachers`
WHERE `phone` IS NULL;


<!-- @qui Utilizzando lo stesso database di ieri, eseguite le query in allegato. Caricate un secondo file nella stessa repo di ieri (db-university) con le query di oggi.
2 file
  -->

  QUERY CON JOIN:

  <!-- TASK 1 -->
  SELECT *
  FROM `students`
  JOIN `degrees`
  ON `students`.`degree_id` = `degrees`.id
  WHERE `degrees`.`name` = "Corso di Laurea in Economia";

  <!-- TASK 2 -->
  SELECT * 
  FROM `degrees`
  JOIN `departments`
  ON `departments`.`id` = `degrees`.`department_id`
  WHERE `degrees`.`level` = "magistrale"
  AND `departments`.`name` = "Dipartimento di Neuroscienze";

  <!-- TASK 3 -->
  SELECT * 
  FROM `courses`
  JOIN `course_teacher` 
  ON `courses`.`id` = `course_teacher`.`course_id`
  JOIN `teachers`
  ON `course_teacher`.`teacher_id` = `teachers`.`id`
  WHERE `teachers`.`id` = 44;

  <!-- TASK 4 -->
  SELECT `degrees`.`name` AS `corso_di_laurea`, 
  `departments`.`name` AS `dipartimento`,
  `students`.`surname` AS `cognome`,
  `students`.`name` AS `nome`
  FROM `students`
  JOIN `degrees`
  ON `degrees`.`id` = `students`.`degree_id`
  JOIN `departments`
  ON `departments`.`id` = `degrees`.`department_id`
  ORDER BY `students`.`surname` ASC, `students`.`name` ASC;

  <!-- TASK 5 -->
  SELECT `degrees`.`name` AS `corso_di_laurea`,
  `courses`.`name` AS `corsi`,
  `teachers`.`surname` AS `cognome`,
  `teachers`.`name` AS `nome`
  FROM `degrees`
  JOIN `courses`
  ON `degrees`.`id` = `courses`.`degree_id`
  JOIN `course_teacher`
  ON `courses`.`id` = `course_teacher`.`course_id`
  JOIN `teachers`
  ON `course_teacher`.`teacher_id` = `teachers`.`id`;

  <!-- TASK 6 -->
  SELECT `teachers`.`surname` AS `cognome`,
  `teachers`.`name` AS `nome`,
  `departments`.`name` AS `dipartimento`
  FROM `departments`
  JOIN `degrees`
  ON `departments`.`id` = `degrees`.`department_id`
  JOIN `courses`
  ON `degrees`.`id` = `courses`.`degree_id`
  JOIN `course_teacher`
  ON `courses`.`id` = `course_teacher`.`course_id`
  JOIN `teachers`
  ON `course_teacher`.`teacher_id` = `teachers`.`id`
  WHERE `departments`.`id` = 5;

  
  QUERY CON GROUP BY

  <!-- TASK 1 -->
  SELECT COUNT(*) AS `iscritti`, YEAR(`enrolment_date`) AS `anno`
  FROM `students`
  GROUP BY YEAR(`students`.`enrolment_date`);

  <!-- TASK 3 -->
  SELECT `exam_student`.`student_id`AS `studenti`,
  AVG (`vote`) AS `media_voti`
  FROM `exam_student`
  GROUP BY `student_id`;

  <!-- TASK 4 -->
  SELECT COUNT(`degrees`.`name`) AS  `corsi_di_laurea`, `degrees`.`department_id` AS `id_dipartimento`
  FROM `degrees`
  GROUP BY `department_id`;


