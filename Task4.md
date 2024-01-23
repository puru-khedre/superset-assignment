# Superset: Task 4

## General key points

* It uses **OLTP** database engines to store informataion of users and dashboard and chrats definitions.

* It is well tested with postgreSQL, mysql, SQLite. While superset supports various databases as *datasources*

## Architecture

![Apache Superset systems architecture](https://cdn-images-1.medium.com/max/1600/0*MZU_QXOxbW8DmbvT.png)

* Gunicorn gateway layer for multiple web server instances with load balancing
* Redis cache layer
* OLTP database like postgreSQL as metadata DB(storing definitions, users, permissions, roles)
* Message queue for async query runs

## Libraries & technology used

1. **SQLAlchemy:** This library is used to connect to various databases and cloud data warehouses (datasources connector)

2. **Gunicorn:** web server gateway interface, mainly used it with django, and flask applications
    * Load balancing
    * uses multiple processes to handle concurrent requests
3. **Redis:** used for data caching and message queues for the async queries
4. **Flask:** python backend of the superset
5. **Celery:** Scheduling jobs and Executing the asynchronous tasks in a distributed and parallel manner
    * celery beat: manage all the workers
    * celery worker: Here the task is executed
6. **React:** library use to creating the frontend of superset
7. **D3:** JS library to create interactive & dynamic visualisation
