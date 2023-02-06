Tags: #sql #database

## What is a relational database?

Реляционная база данных организует данные в строки и столбцы, которые в совокупности образуют таблицу. Данные структурированы по нескольким таблицам, которые объединены с помощью первичного ключа или внешнего ключа. Эти уникальные идентификаторы демонстрируют различные виды отношений, существующие между таблицами.

## What is SQL?

**SQL** (Structured Query Language) - язык запросов для получения из базы данных необходимой информации.

SQL-operators - некие слова и символы, которые используются для выполнения конкретной операции с данными в БД.

Операторы выделяются на несколько групп:

- DDL (Data Definition Language) - работают с целыми таблицами:
	- `CREATE` - создание объекта в БД;
	- `ALTER` - изменение объекта;
	- `DROP` - удаление объекта.
- DML (Data Manipulation Language) - работают с содержимым таблиц:
	- `SELECT` - выбор данных с условием;
	- `INSERT` - добавление новых данных;
	- `UPDATE` - изменение данных;
	- `DELETE` - удаление данных.
- DCL (Data Control Language) - определение доступа к данным:
	- `GRANT` - предоставление доступа;
	- `REVOKE` - отзыв выданного доступа;
	- `DENY` - запрет доступа.
- TCL (Transaction Control Language) - управление транзакциями:
	- `BEGIN TRANSACTION` - начало транзакции;
	- `COMMIT TRANSACTION` - изменение команд внутри транзакции;
	- `ROLLBACK TRANSACTION` - откат транзакции;
	- `SAVE TRANSACTION` - промежуточная точка сохранения внутри транзакции.
