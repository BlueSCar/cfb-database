# cfb-database
College football database - data store for all sorts of data and statistics pertaining to college football


# contents
1. [description](#description)
2. [import](#import)
3. [data](#data)
4. [schema diagram](#diagram)
5. [future](#future)
6. [license](#license)

# description
This is a PostgreSQL database meant for housing all sorts of data pertaining to college football.  It is a work-in-progress that aspires to be a comprehensive dataset.  It is designed for use in all sorts of data analysis and machine learning.

# import
The SQL Dump file can be downloaded from [this link](https://drive.google.com/open?id=1yqc5uocKmWui8kvXl0RENSlQbtWkwwY2).

To restore the dump file, follow the below steps. It is presumed that you have PostgreSQL installed on your machine as the dump file will only work with PostgreSQL.

Please note that you shouldn't have to create any schema or parse out any data. The SQL dump restore tool should do everything for you. You only need to create a blank database and a user with ownership over that database.

If you still have questions or concerns with using the restore tool, here are some steps (copied from the previous post) that have been verified to work.

## create an empty databse
Run the following command to create an empty database (if you are on Windows, you may need to cd to the bin folder for Postgres in Program Files).

```bash
createdb -T template0 cfb
```

## create user (optional)
It is recommened to create a user named 'reddit' as owner of the database. To do that, go into SQL Shell and run these commands:

```sql
CREATE ROLE reddit WITH LOGIN PASSWORD <your password here>;
ALTER ROLE reddit CREATEDB;
GRANT ALL PRIVILEGES ON DATABASE cfb TO reddit;
```

## restore the sql dump
Restore the backup. From bash/cmd/what-have-you, run this command:

```bash
psql -U reddit cfb < /path/to/sql/dump/file.sql
```

# data
This is a non-comprehensive list of data currently included.  New types of data are frequently being added. The data is current as of the end of the 2017 season and national championship game.

- game data
- drive data
- play by play data
- team data
    - colors
    - names
- team talent data
- player data
    - hometown
    - position
    - height/weight
- head coach data and records
- player game statistics
- team game statistics
- venue data

# diagram
![Schema Diagram](https://github.com/BlueSCar/cfb-database/blob/master/SchemaDiagram.png "Schema")

# future
This is a semi-prioritized non-comprehensive list of planned features.

- Recruiting data (247 Composite)
- Player-Play associations
- Conference and division data
- Betting lines
- Weather
- Accessibility (i.e. public hosting or a public API)
- Real-time updates

# license

MIT