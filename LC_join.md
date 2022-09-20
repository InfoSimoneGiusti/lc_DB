Selezionare tutti i corsi del Corso di Laurea in Informatica (22)
SELECT `degrees`.`id` AS "degree_id", `period`, `courses`.`name`, `year`
FROM `degrees`
JOIN `courses`
ON `courses`.`degree_id` = `degrees`.`id`
WHERE `degrees`.`name` = "Corso di Laurea in Informatica";



Selezionare le informazioni sul corso con id = 144, con tutti i relativi appelli d’esame
SELECT `courses`.`name` as "nome_corso", `period`, `date`, `hour`, `location`, `address`, `exams`.`id` as "id_esame"
FROM `courses`
JOIN `exams`
ON `courses`.`id` = `exams`.`course_id`
WHERE `courses`.`id` = 144;



Selezionare a quale dipartimento appartiene il Corso di Laurea in Diritto dell'Economia (Dipartimento di Scienze politiche, giuridiche e studi internazionali)
SELECT `departments`.`name`
FROM `degrees`
JOIN `departments`
ON `degrees`.`department_id` = `departments`.`id`
WHERE `degrees`.`name` = "Corso di Laurea in Diritto dell'Economia";


Selezionare tutti gli appelli d'esame del Corso di Laurea Magistrale in Fisica del primo anno
SELECT `exams`.`id`, `exams`.`date`,`exams`.`hour`,`exams`.`location`,`exams`.`address`
FROM `exams`
JOIN `courses` ON `exams`.`course_id` = `courses`.`id`
JOIN `degrees` ON `degrees`.`id` = `courses`.`degree_id`
WHERE `degrees`.`name` = "Corso di Laurea Magistrale in Fisica"
AND `courses`.`year` = 1



Selezionare tutti i docenti che insegnano nel Corso di Laurea in Lettere (21)
SELECT DISTINCT `teachers`.`name`, `teachers`.`surname`, `teachers`.`phone`
FROM `teachers`
JOIN `course_teacher` ON `teachers`.`id` = `course_teacher`.`teacher_id`
JOIN `courses` ON `courses`.`id` = `course_teacher`.`course_id`
JOIN `degrees` ON `degrees`.`id` = `courses`.`degree_id`
WHERE `degrees`.`name` = "Corso di Laurea in Lettere"  
ORDER BY `teachers`.`name` ASC;



Selezionare il libretto universitario di Mirco Messina (matricola n. 620320)
SELECT `courses`.`name`, `exams`.`date`, `exams`.`hour`, `exams`.`location`, `exams`.`address`, `exam_student`.`vote` 
FROM `courses`
JOIN `exams` ON `exams`.`course_id` = `courses`.`id`
JOIN `exam_student` ON `exam_student`.`exam_id` = `exams`.`id`
JOIN `students` ON `students`.`id` = `exam_student`.`student_id`
WHERE `students`.`registration_number` = "620320"
AND `exam_student`.`vote` >= 18;



Selezionare il voto medio di superamento d'esame per ogni corso, con anche i dati del corso di laurea associato, ordinati per media voto decrescente
SELECT AVG(exam_student.vote) AS "voto_medio", `courses`.`name` AS "nome_corso", `degrees`.`name` AS "nome_laurea" 
FROM `degrees` 
JOIN `courses` ON `degrees`.`id` = `courses`.`degree_id` 
JOIN `exams` ON `courses`.`id` = `exams`.`course_id` 
JOIN `exam_student` ON `exam_student`.`exam_id` = `exams`.`id` 
WHERE `exam_student`.`vote` >= 18 
GROUP BY `courses`.`id` 
ORDER BY `voto_medio` DESC;