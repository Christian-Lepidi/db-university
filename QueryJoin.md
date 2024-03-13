# Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

SELECT `students`.\*, `degrees`.`name` FROM `students` INNER JOIN `degrees` ON `degrees`.`id` = `students`.`degree_id`WHERE `degrees`.`name`= 'Corso di Laurea in Economia';

# Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

SELECT `degrees`. \*, `departments`.`name` FROM `degrees` INNER JOIN `departments` ON `departments`.`id`= `degrees`.`department_id` WHERE `departments`.`name`= 'Dipartimento di Neuroscienze' AND `degrees`.`level`='magistrale';

# Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

SELECT `courses`. \*,`teachers`.`name`,`teachers`.`surname` FROM `courses` INNER JOIN `course_teacher` ON `courses`.`id`= `course_teacher`.`course_id` INNER JOIN `teachers` ON `teachers`.`id` = `course_teacher`.`teacher_id` WHERE `teachers`.`name`='Fulvio' AND `teachers`.`surname`='Amato';

# Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

SELECT `students`.`surname`,`students`.`name`,`degrees`. \*,`departments`.`name` FROM `students` INNER JOIN `degrees` ON `degrees`.`id`= `students`.`degree_id` INNER JOIN `departments` ON `departments`.`id` = `degrees`.`department_id` ORDER BY `students`.`surname`ASC;

# Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

# Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

SELECT `teachers`. \*
FROM `teachers`
INNER JOIN `course_teacher`
ON `teachers`.`id` = `course_teacher`.`teacher_id`
INNER JOIN `courses`
ON `courses`.`id` = `course_teacher`.`course_id`
INNER JOIN `degrees`
ON `degrees`.`id` = `courses`.`degree_id`
INNER JOIN `departments`
ON `departments`.`id` = `degrees`.`department_id`
WHERE `departments`.`name` = "Dipartimento di Matematica";

# BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente,filtrare i tentativi con voto minimo 18.
