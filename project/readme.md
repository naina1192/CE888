This folder contains information about the text pre-processing steps of the Spider Dataset
Data :

Download the data from the Spider official website https://yale-lily.github.io/spider


Data Content and Format Question, SQL, and Parsed SQL
Each file in train.json,dev.json, and train_others.json contains the following fields:

question: the natural language question
question_toks: the natural language question tokens
db_id: the database id to which this question is addressed.
query: the SQL query corresponding to the question.
query_toks: the SQL query tokens corresponding to the question.
sql: parsed results of this SQL query using process_sql.py. Please refer to parsed_sql_examples.sql in thepreprocess directory for the detailed documentation.
 {
        "db_id": "world_1",
        "query": "SELECT avg(LifeExpectancy) FROM country WHERE Name NOT IN (SELECT T1.Name FROM country AS T1 JOIN countrylanguage AS T2 ON T1.Code  =  T2.CountryCode WHERE T2.Language  =  \"English\" AND T2.IsOfficial  =  \"T\")",
        "query_toks": ["SELECT", "avg", "(", "LifeExpectancy", ")", "FROM", ...],
        "question": "What is average life expectancy in the countries where English is not the official language?",
        "question_toks": ["What", "is", "average", "life", ...],
        "sql": {
            "except": null,
            "from": {
                "conds": [],
                "table_units": [
                    ...
            },
            "groupBy": [],
            "having": [],
            "intersect": null,
            "limit": null,
            "orderBy": [],
            "select": [
                ...
            ],
            "union": null,
            "where": [
                [
                    true,
                    ...
                    {
                        "except": null,
                        "from": {
                            "conds": [
                                [
                                    false,
                                    2,
                                    [
                                    ...
                        },
                        "groupBy": [],
                        "having": [],
                        "intersect": null,
                        "limit": null,
                        "orderBy": [],
                        "select": [
                            false,
                            ...
                        "union": null,
                        "where": [
                            [
                                false,
                                2,
                                [
                                    0,
                                   ...
        }
    },

Tables
tables.json contains the following information for each database:

db_id: database id
table_names_original: original table names stored in the database.
table_names: cleaned and normalized table names. We make sure the table names are meaningful. [to be changed]
column_names_original: original column names stored in the database. Each column looks like: [0, "id"]. 0 is the index of table names in table_names, which is city in this case. "id" is the column name.
column_names: cleaned and normalized column names. We make sure the column names are meaningful. [to be changed]
column_types: data type of each column
foreign_keys: foreign keys in the database. [3, 8] means column indices in the column_names. These two columns are foreign keys of two different tables.
primary_keys: primary keys in the database. Each number is the index of column_names.
