camper@codespaces-40f539:/workspace/project$ psql --username=freecodecamp --dbname=postgres
psql (12.22 (Ubuntu 12.22-0ubuntu0.20.04.4))
Type "help" for help.

postgres=> CREATE DATABASE salon;
CREATE DATABASE
postgres=> \c salon
You are now connected to database "salon" as user "freecodecamp".
salon=> CREATE TABLE customers (
salon(>   customer_id SERIAL PRIMARY KEY,
salon(>   phone VARCHAR(20) UNIQUE NOT NULL,
salon(>   name VARCHAR(50) NOT NULL
salon(> );
CREATE TABLE
salon=> CREATE TABLE services (
salon(>   service_id SERIAL PRIMARY KEY,
salon(>   name VARCHAR(50) NOT NULL
salon(> );
CREATE TABLE
salon=> CREATE TABLE appointments (
salon(>   appointment_id SERIAL PRIMARY KEY,
salon(>   customer_id INT REFERENCES customers(customer_id),
salon(>   service_id INT REFERENCES services(service_id),
salon(>   time VARCHAR(20) NOT NULL
salon(> );
CREATE TABLE
salon=> INSERT INTO services(name) VALUES('cut'), ('color'), ('perm'), ('style'), ('trim');camper: /project$ touch salon.sh
camper: /project$ chmod +x salon.sh
camper: /project$ ./salon.sh
~~~~~ MY SALON ~~~~~

Welcome to My Salon, how can I help you?
1) cut
2) color
3) perm
4) style
5) trim
pg_dump -cC --inserts -U freecodecamp salon > salon.sql
