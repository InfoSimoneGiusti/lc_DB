/--SELECT--/

1. Selezionare tutti gli insegnanti
SELECT * 
FROM `teachers`;

2. Selezionare tutti i referenti per ogni dipartimento
SELECT `name`, `head_of_department` 
FROM `departments`;

3. Selezionare tutti gli studenti il cui nome inizia per "E" (373)
SELECT * 
FROM `students` 
WHERE `name` LIKE "E%";

4. Selezionare tutti gli studenti che si sono iscritti nel 2021 (734)
SELECT * FROM `students` 
WHERE YEAR(enrolment_date) = 2021;

5. Selezionare tutti i corsi che non hanno un sito web (676)
SELECT * FROM `courses` WHERE `website` IS NULL;


6. Selezionare tutti gli insegnanti che hanno un numero di telefono (50)
SELECT * FROM `teachers` WHERE `phone` IS NOT NULL;


7. Selezionare tutti gli appelli d'esame dei mesi di giugno e luglio 2020 (2634)
SELECT *
FROM `exams` 
WHERE `date` >= "2020-06-01"
AND `date` <= "2020-07-31";

SELECT *
FROM `exams` 
WHERE `date` BETWEEN "2020-06-01" AND "2020-07-31";


8. Qual è il numero totale degli studenti iscritti? (5000)
SELECT COUNT(*) AS "numero_studenti" FROM `students`;





/--GROUP BY--/


1. Contare i corsi raggruppati per cfu
SELECT COUNT(*), `cfu` 
FROM `courses` 
GROUP BY `cfu`;


2. Contare gli studenti raggruppati per anno di nascita
SELECT COUNT(*) AS 'numero_studenti', YEAR(`date_of_birth`) AS "anno_nascita"
FROM `students`
GROUP BY YEAR(`date_of_birth`);

3. Selezionare il voto più basso dato ad ogni appello d'esame
SELECT MIN(`vote`) AS "voto_piu_basso", `exam_id` 
FROM `exam_student` 
GROUP BY `exam_id`;


4. Contare gli appelli d'esame del mese di luglio raggruppati per giorno
SELECT COUNT(*) AS "numero_appelli", DAY(`date`) AS "giorno"
FROM `exams`
WHERE MONTH(`date`) = 7
GROUP BY DAY(`date`);