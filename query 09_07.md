Group by:

1. Contare quanti iscritti ci sono stati ogni anno

```sql
SELECT COUNT(*) AS "number_of_students", YEAR(enrolment_date) AS "enrolment_year"
FROM `students`
GROUP BY `enrolment_year`;
```

2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio

```sql
SELECT COUNT(*) AS "number_of_teachers", `office_address`
FROM `teachers`
GROUP BY `office_address`;
```

3. Calcolare la media dei voti di ogni appello d'esame

```sql
SELECT AVG(`vote`) AS "average rating", `exam_id`
FROM `exam_students`
GROUP BY `exam_id`;
```

4. Contare quanti corsi di laurea ci sono per ogni dipartimento

```sql
SELECT COUNT(*) AS "degree_courses_for_each_department", `department_id`
FROM `degrees`
GROUP BY `department_id`;
```

Join:

1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

```sql
SELECT `students`.*,
`degrees`.`name` AS "degree_name"
FROM `students`
JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id`
WHERE `degrees`.`name`= "Corso di Laurea in Economia";
```

2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

```sql
SELECT `degrees`.*,
`departments`.`name` AS "departments_name"
FROM `degrees`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
WHERE `degrees`.`level` = "magistrale"
AND `departments`.`name` = "Dipartimento di Neuroscienze";
```

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

```sql
SELECT `courses`.*
FROM `courses`
JOIN `course_teacher` ON `courses`.`id` = `course_teacher`.`course_id`
WHERE `course_teacher`.`teacher_id` = 44;
```

4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

```sql
SELECT `students`.`surname` AS "student_surname",
`students`.`name` AS "student_name",
`students`.`registration_number`,
`students`.`email`,
`degrees`.`name` AS "degrees_name",
`degrees`.`level`,
`degrees`.`address`,
`degrees`.`email`,
`degrees`.`website`,
`departments`.`name` AS "departments_name",
`departments`.`head_of_department`
FROM `students`
JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
ORDER BY `student_surname`, `student_name`;
```

5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

```sql
SELECT `degrees`.`name` AS "degree_name",
`courses`.`name` AS "course_name",
`teachers`.`name` AS "teacher_name"
FROM `degrees`
JOIN `courses` ON `degrees`.`id` = `courses`.`degree_id`
JOIN `course_teacher` ON `courses`.`id` = `course_teacher`.`course_id`
JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id`;
```

6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

```sql
SELECT DISTINCT `teachers`.*,
`departments`.`name` AS "departments_name"
FROM `teachers`
JOIN `course_teacher` ON `course_teacher`.`teacher_id` = `teachers`.`id`
JOIN `courses` ON `course_teacher`.`course_id` = `courses`.`id`
JOIN `degrees` ON `courses`.`degree_id` = `degrees`.`id`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
WHERE `departments`.`name` = "Dipartimento di Matematica";
```

7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.

```sql

```
