<!-- Copyright 2025 Maxime Jan <maxime.jan@edufr.ch> -->
<!-- SPDX-License-Identifier: CC-BY-NC-SA-4.0 -->

```{metadata}
solutions: dynamic
```
# Exercices SELECT

Téléchargez la [base de données](university_pk_fk.db) d'une université et ouvrez la avec DB Browser for SQLite. En utilisant des requêtes SELECT ... FROM ... WHERE ... répondez aux questions suivantes.

```{image} images/university_schema.png
:width: 50%
:alt: Schéma relationnel de la base de données des films
:align: center
```


```{role} input(quiz-input)
:right: width: 18rem; clear: right;
:check: split lowercase
```

```{quiz}
1.  {input}`1504`
    Quel est le numéro d'étudiant de Dayanis Oldehaver ?
2.  {input}`r102`
    En quelle salle est donné le cours « Database systems » ?
3.  {input}`132`
    Combien d'étudiants ont 23 ans ou plus ?
4.  {input}`Engineering drawing,Materials engineering`
    {input}`Engineering drawing,Materials engineering`
    Quels sont les deux cours donnés en R201 ?
5.  {input}`Condensed matter physics`
    Quel cours commence à 14h en salle R403 ?
6.  {input}`28`
    Combien d'étudiants sont inscrits au cours  « Relativity » ?
7.  {input}`36`
    Combien d’étudiants en année « Freshman » (FR) étudient soit la physique,
    soit les maths ?
8.  {input}`Blythe Raskop`
    Quel est le nom complet de l'étudiant dont le nom commence par « Bly » ?
9.  {input}`186`
    Combien d'élèves sont inscrits dans un cours ayant le mot « engineering »
    dans leur nom ?
10. {input}`9`
    Combien de directeurs de faculté (FNAME) ont un « x » ou un « y » dans leur
    nom ?
11. {input}`129`
    Combien d’élèves ont entre 17 et 20 ans (y compris) et sont en années « FR »
    ou « SO » ?
```

````{solution}
```{code-block} text
:linenos:
--1
select SNUM from student
where sname like '%Daya%';
--ou
select SNUM from student
where sname = 'Dayanis Oldehaver';
--1504

--2
select room from course
where cname = 'Database systems';
--R102

--3
select count(*) from student
where age >=23;
--132

--4
select CNAME from course
where room = 'R201';
--Materials engineering
--Engineering drawing

--5
select * from course
where room = 'R403'
and MEETS_AT = '14:00:00';
--Condensed matter physics

--6
select count(*) from enrolled
where cname = 'Relativity';
--28

--7
select count(*) from student
where YEAR = 'FR'
and (major = 'PHY' or major = 'MA');

--ou
select count(*) from student
where YEAR = 'FR'
and major in ('PHY','MA');
--36

--8
select * from student
where sname like 'Bly%';
--Blythe Raskop
--ici, nous ne mettons pas de % au début, 
--car nous recherchons des noms qui commencent par "Bly", 
--nous n'attendons donc rien avant le texte "Bly", mais seulement après.

--9
select count(*) from enrolled
where cname like '%engineering%';
--186

--10
select count(*) from faculty
where fname like '%x%'
or fname like '%y%';

--11
select count(*) from student
where age >=17 and age <=20
and (year = 'FR' or year = 'SO');
--Ici, les parenthèses sont obligatoires pour respecter la logique demandée 
--dans la question. Sans elles, nous sélectionnerions tous les élèves 
--de la classe 'SO', sans tenir compte de leur âge.

--ou
select count(*) from student
where age >=17 and age <=20
and year in('FR','SO');
--129
```

````

<!-- pour 7 select count(*) from student
join enrolled on student.SNUM = enrolled.SNUM
where student.YEAR = 'FR'
and cname like '%math%'
or cname like '%physics%' -->