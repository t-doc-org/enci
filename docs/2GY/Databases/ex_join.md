```{metadata}
solutions: dynamic
```
# Exercices JOIN

Si vous ne l'avez pas déjà, téléchargez la [base de données](university_pk_fk.db) d'une université et ouvrez la avec DB Browser for SQLite. En utilisant des requêtes SELECT ... FROM ... JOIN ... WHERE ... répondez aux questions suivantes.

```{image} images/university_schema.png
:width: 50%
:alt: Schéma relationnel de la base de données des films
:align: center
```

```{role} input(quiz-input)
:right: width: 18rem;
:check: lowercase
```

```{quiz}
1.  {input}`Electromagnetism and electronics`
    A quels cours est inscrit l’élève dont le nom commence par « Denys » ?
2.  {input}`Medicinal chemistry,Physical chemistry`
    Quel est le cours du département numéro « 2 » qui commence à 9h00 ? (Donnenz un résultat correct s'il existe plusieurs possibilités.)
3.  {input}`Etelvino Lanzoni`
    Quel est le nom du directeur de la faculté (FNAME) à laquelle appartient le cours « Engineering drawing » ?
4.  {input}`133`
    Combien d’élèves distincts sont inscrits dans un cours qui a lieu en salle
    R403, vous devriez commencer par select count(distinct snum)...?
5.  {input}`28`
    Combien d’élèves distincts qui ont cours en salle R403 sont en année
    « FR » ?
6.  {input}`Aleksandrov Nemeth`
    Quel est le nom du directeur de faculté, du cours auquel 'Feng' est
    inscrit ?
```

````{solution}
```{code-block} text
:linenos:
--1
select cname from enrolled
join student on enrolled.snum = student.SNUM
where sname like 'Denys%';
--Electromagnetism and electronics
--sans JOIN
select snum from student
where sname like 'Denys%';
--1113
select cname from enrolled
where snum = 1113;
--ou avec requêtes imbriquées
select cname from enrolled
where snum in (select snum from student
where sname like 'Denys%');

--2
select cname from course
join faculty on course.fid = faculty.FID
where deptid = 2 and MEETS_AT = '09:00:00';
--Physical chemistry
--Medicinal chemistry

--3
select FNAME from faculty
join course on course.fid = faculty.FID
where cname = "Engineering drawing";

--4
select count(distinct snum) from enrolled
join course on course.cname = enrolled.CNAME
where room = 'R403';
--133 

--5
select count(distinct enrolled.snum) from enrolled
join course on course.cname = enrolled.CNAME
join student on enrolled.snum = student.SNUM
where room = 'R403'
and student.year ='FR';
--28

--6
select fname from faculty
join course on course.fid = faculty.FID
join enrolled on course.cname = enrolled.CNAME
join student on enrolled.SNUM = student.SNUM
where student.SNAME like '%Feng%';
--Aleksandrov Nemeth
```

````

Pour plus d'exercices, vous pouvez consulter la page de mon collègue : Maxime Jan [Joindre plusieurs tables, Exercices de Maxime Jan](https://janm.t-doc.org/DOI2/Databases/sql_join.html#exercices). (Notez qu'il s'agit d'un site web différent, commençant par « janm », donc une fois que vous avez terminé les exercices qui s'y trouvent, retournez sur le site commençant par « enci »).
