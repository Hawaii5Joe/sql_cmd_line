<!-- EASY -->
<!-- 1. First and last name only -->
    mysql> select first_name, last_name from student;
        +------------+-----------+
        | first_name | last_name |
        +------------+-----------+
        | Eric       | Ephram    |
        | Greg       | Gould     |
        | Adam       | Ant       |
        | Howard     | Hess      |
        | Charles    | Caldwell  |
        | James      | Joyce     |
        | Doug       | Dumas     |
        | Kevin      | Kraft     |
        | Frank      | Fountain  |
        | Brian      | Biggs     |
        +------------+-----------+
        10 rows in set (0.00 sec)

<!-- 2. Students with less than 8 years exp -->
    mysql> select * from student where years_of_experience <8 order by years_of_experience asc;
        +------------+------------+-----------+---------------------+------------+
        | student_id | first_name | last_name | years_of_experience | start_date |
        +------------+------------+-----------+---------------------+------------+
        |          4 | Howard     | Hess      |                   1 | 2016-02-28 |
        |          1 | Eric       | Ephram    |                   2 | 2016-03-31 |
        |          8 | Kevin      | Kraft     |                   3 | 2016-04-15 |
        |         10 | Brian      | Biggs     |                   4 | 2015-12-25 |
        |          3 | Adam       | Ant       |                   5 | 2016-06-02 |
        |          2 | Greg       | Gould     |                   6 | 2016-09-30 |
        |          5 | Charles    | Caldwell  |                   7 | 2016-05-07 |
        +------------+------------+-----------+---------------------+------------+
    7 rows in set (0.00 sec)

<!-- 3. sort by last name asc -->
    mysql> select last_name, start_date, student_id from student order by last_name asc;
        +-----------+------------+------------+
        | last_name | start_date | student_id |
        +-----------+------------+------------+
        | Ant       | 2016-06-02 |          3 |
        | Biggs     | 2015-12-25 |         10 |
        | Caldwell  | 2016-05-07 |          5 |
        | Dumas     | 2016-07-04 |          7 |
        | Ephram    | 2016-03-31 |          1 |
        | Fountain  | 2016-01-31 |          9 |
        | Gould     | 2016-09-30 |          2 |
        | Hess      | 2016-02-28 |          4 |
        | Joyce     | 2016-08-27 |          6 |
        | Kraft     | 2016-04-15 |          8 |
        +-----------+------------+------------+
        10 rows in set (0.00 sec)

<!-- 4. Adam james frank -->
    mysql> select * from student where first_name in ("Adam","James","Frank") order by last_name desc;
        +------------+------------+-----------+---------------------+------------+
        | student_id | first_name | last_name | years_of_experience | start_date |
        +------------+------------+-----------+---------------------+------------+
        |          6 | James      | Joyce     |                   9 | 2016-08-27 |
        |          9 | Frank      | Fountain  |                   8 | 2016-01-31 |
        |          3 | Adam       | Ant       |                   5 | 2016-06-02 |
        +------------+------------+-----------+---------------------+------------+
        3 rows in set (0.00 sec)

<!-- 5. Between 1/1/16-6/30/16 -->
    mysql> SELECT first_name, last_name, start_date FROM student WHERE start_date BETWEEN "2016-01-01" AND "2016-06-30" ORDER BY start_date DESC;
        +------------+-----------+------------+
        | first_name | last_name | start_date |
        +------------+-----------+------------+
        | Adam       | Ant       | 2016-06-02 |
        | Charles    | Caldwell  | 2016-05-07 |
        | Kevin      | Kraft     | 2016-04-15 |
        | Eric       | Ephram    | 2016-03-31 |
        | Howard     | Hess      | 2016-02-28 |
        | Frank      | Fountain  | 2016-01-31 |
        +------------+-----------+------------+
        6 rows in set (0.00 sec)

<!-- MEDIUM -->
    mysql> explain assignment;
        +----------------+------------------+------+-----+---------+----------------+
        | Field          | Type             | Null | Key | Default | Extra          |
        +----------------+------------------+------+-----+---------+----------------+
        | assignment_id  | int(11) unsigned | NO   | PRI | NULL    | auto_increment |
        | student_id     | int(11)          | NO   |     | NULL    |                |
        | assignment_nbr | int(11)          | NO   |     | NULL    |                |
        | class_id       | int(11)          | YES  |     | NULL    |                |
        | grade_id       | int(11) unsigned | NO   | MUL | NULL    |                |
        +----------------+------------------+------+-----+---------+----------------+
        5 rows in set (0.00 sec)

    mysql> select * from assignment;
        +---------------+------------+----------------+----------+----------+
        | assignment_id | student_id | assignment_nbr | class_id | grade_id |
        +---------------+------------+----------------+----------+----------+
        |             1 |          1 |             23 |       34 |        1 |
        |             2 |          1 |             23 |       34 |        1 |
        |             3 |          2 |             23 |       98 |        2 |
        |             4 |          3 |             45 |       56 |        3 |
        |             5 |          4 |             56 |       67 |        4 |
        |             6 |          5 |             67 |       54 |        5 |
        +---------------+------------+----------------+----------+----------+
        6 rows in set (0.00 sec)

    mysql> explain grade;
        +-------------+------------------+------+-----+---------+----------------+
        | Field       | Type             | Null | Key | Default | Extra          |
        +-------------+------------------+------+-----+---------+----------------+
        | id          | int(11) unsigned | NO   | PRI | NULL    | auto_increment |
        | grade_value | varchar(30)      | YES  |     | NULL    |                |
        +-------------+------------------+------+-----+---------+----------------+
        2 rows in set (0.00 sec)

    mysql> select * from grade;
        +----+-----------------------------+
        | id | grade_value                 |
        +----+-----------------------------+
        |  1 | Incomplete                  |
        |  2 | Complete and unsatisfactory |
        |  3 | Complete and satisfactory   |
        |  4 | Exceeds expectations        |
        |  5 | Not graded                  |
        +----+-----------------------------+
        5 rows in set (0.00 sec)

<!-- HARD -->
    mysql> explain student;
        +---------------------+------------------+------+-----+---------+----------------+
        | Field               | Type             | Null | Key | Default | Extra          |
        +---------------------+------------------+------+-----+---------+----------------+
        | student_id          | int(11) unsigned | NO   | PRI | NULL    | auto_increment |
        | first_name          | varchar(30)      | YES  |     | NULL    |                |
        | last_name           | varchar(30)      | YES  |     | NULL    |                |
        | years_of_experience | tinyint(3)       | YES  |     | NULL    |                |
        | start_date          | date             | YES  |     | NULL    |                |
        +---------------------+------------------+------+-----+---------+----------------+
        5 rows in set (0.00 sec)

    mysql> explain assignment;
        +----------------+------------------+------+-----+---------+----------------+
        | Field          | Type             | Null | Key | Default | Extra          |
        +----------------+------------------+------+-----+---------+----------------+
        | assignment_id  | int(11) unsigned | NO   | PRI | NULL    | auto_increment |
        | student_id     | int(11) unsigned | NO   | MUL | NULL    |                |
        | assignment_nbr | int(11)          | NO   |     | NULL    |                |
        | class_id       | int(11)          | YES  |     | NULL    |                |
        | grade_id       | int(11) unsigned | NO   | MUL | NULL    |                |
        +----------------+------------------+------+-----+---------+----------------+
        5 rows in set (0.00 sec)

mysql> insert into assignment (student_id, assignment_nbr, class_id, grade_id) VALUES ("20","34","44","30");
ERROR 1452 (23000): Cannot add or update a child row: a foreign key constraint fails (`tiy`.`assignment`, CONSTRAINT `fk_grade_id` FOREIGN KEY (`grade_id`) REFERENCES `grade` (`id`))
