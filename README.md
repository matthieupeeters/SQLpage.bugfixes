<h1 align="center">SQLpage</h1>

[![A short video explaining the concept of sqlpage](./docs/sqlpage.gif)](./docs/sqlpage.mp4)

SQLPage is an [**SQL**](https://en.wikipedia.org/wiki/SQL)-only webapp builder.
It is meant for data scientists, analysts, and business intelligence teams
to build powerful data-centric applications quickly,
without worrying about any of the traditional web programming languages and concepts.

With SQLPage, you write simple `.sql` files containing queries to your database
to select, group, update, insert, and delete your data, and you get good-looking clean webpages
displaying your data as text, lists, grids, plots, and forms.

## Supported databases

 - [sqlite](https://www.sqlite.org/index.html)
 - [PostgreSQL](https://www.postgresql.org/), and other compatible databases such as *CockroachDB* and *Aurora*.
 - [MySQL](https://www.mysql.com/), and other compatible databases such as *MariaDB* and *TiDB*. 

## How it works

SQLPage is a [web server](https://en.wikipedia.org/wiki/Web_server) written in 
[rust](https://en.wikipedia.org/wiki/Rust_(programming_language)).
When it receives a request to a URL ending in `.sql`, it finds the corresponding
SQL file, runs it on the database,
passing it information from the web request as SQL statement parameters.
When the database starts returning rows for the query,
SQLPage maps each piece of information in the row to a parameter 
in one of its pre-defined components' templates, and streams the result back
to the user's browser.

## Get started

 - [Install docker](https://docs.docker.com/get-docker/)
 - In a terminal, run the following command: `docker run -it --name sqlpage -p 8080:8080 --volume "$(pwd):/var/www" --rm lovasoa/sqlpage`
 - Create a file called index.sql with the contents from [this example](./index.sql) 
 - Open https://localhost:8080 in your browser

## Technologies and libraries used

 - [actix web](https://actix.rs/) handles HTTP requests at an incredible speed,
 - [tabler](https://preview.tabler.io) handles the styling for professional-looking clean components,
 - [tabler icons](https://tabler-icons.io) is a large set of icons you can select directly from your SQL,
 - [handlebars](https://handlebarsjs.com/guide/) render HTML pages from readable templates for each component.
