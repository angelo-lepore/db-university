// Modellizzare la struttura di un database per memorizzare tutti i dati riguardanti una università:

- sono presenti diversi `Dipartimenti` (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);
- ogni `Dipartimento` offre più `Corsi di Laurea` (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
- ogni `Corso di Laurea` prevede diversi `Corsi` (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
- ogni `Corso` può essere tenuto da diversi `Insegnanti`;
- ogni `Corso` prevede più appelli d'`Esame`;
- ogni `Studente` è iscritto ad un solo `Corso di Laurea`;
- ogni `Studente` può iscriversi a più appelli di `Esame`;
- per ogni appello d'`Esame` a cui lo `Studente` ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente.
<!-- Pensiamo a quali entità (tabelle) creare per il nostro database e cerchiamo poi di stabilirne le relazioni. Infine, andiamo a definire le colonne e i tipi di dato di ogni tabella. -->

## students

-id
-name
-surname
-student_code

### detail_student

-id
-student_id
-mail
-phone
-address

## teachers

-id
-name
-surname
-teacher_code
-subject

### detail_teacher

-id
-teacher_id
-mail
-phone
-address

## departments

-id
-name
-department_code
-department_address

## degree_course

-id
-department_id
-name
-degree_course_code

## course

-id
-name
-course_length
-course_credits

## exams

-id
-student_id
-teacher_id
-course_id
-date
-subscribers

## results

-id
-student_id
-exam_id
-type_of_exam
-vote
