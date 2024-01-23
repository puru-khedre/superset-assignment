# Superset: Task 4

## General key points

* It uses **OLTP** database engines to store information about users, dashboard and chart definitions.

* It is well-tested with PostgreSQL, MySQL, and SQLite. While superset supports various databases as *data sources*

## Architecture

![Apache Superset systems architecture](https://cdn-images-1.medium.com/max/1600/0*MZU_QXOxbW8DmbvT.png)

* Gunicorn gateway layer for multiple web server instances with load balancing
* Redis cache layer
* OLTP database like PostgreSQL as metadata DB(storing definitions, users, permissions, roles)
* Message queue for async query runs

## Libraries & technology used

1. **SQLAlchemy:** This library is used to connect to various databases and cloud data warehouses (data sources connector)

2. **Gunicorn:** web server gateway interface, mainly used with Django, and Flask applications
    * Load balancing
    * uses multiple processes to handle concurrent requests
3. **Redis:** used for data caching and message queues for the async queries
4. **Flask:** python backend of the superset
5. **Celery:** Scheduling jobs and Executing the asynchronous tasks in a distributed and parallel manner
    * celery beat: manage all the workers
    * celery worker: Here the task is executed
6. **React:** library used to create the frontend of superset
7. **D3:** JS library to create interactive & dynamic visualisation
