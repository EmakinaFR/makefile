Makefile for Symfony 4
======================

The following commands can be listed by typing **make** in your terminal at the root of your project.

Available commands
------------------

### Project setup

| Command | Description                                                       |
| ------- | ----------------------------------------------------------------- |
| clear   | Remove all the cache, the logs, the sessions and the built assets |
| clean   | Clear and remove dependencies                                     |
| cc      | Clear the cache in dev env                                        |

### Database

| Command     | Description                                                                         |
| ----------- | ----------------------------------------------------------------------------------- |
| db-diff     | Generate a migration by comparing your current database to your mapping information |
| db-migrate  | Migrate database schema to the latest available version                             |
| db-update   | Force database update                                                               |
| db-rollback | Rollback the latest executed migration                                              |
| db-load     | Reset the database fixtures                                                         |
| db-validate | Check the ORM mapping                                                               |

### Assets

| Command     | Description                                                    |
| ----------- | -------------------------------------------------------------- |
| watch       | Watch the assets and build their development version on change |
| assets      | Build the development version of the assets                    |
| assets-prod | Build the production version of the assets                     |

### Dependencies

| Command | Description                                 |
| ------- | ------------------------------------------- |
| deps    | Install the project PHP and JS dependencies |

### Tests

| Command  | Description                                    |
| -------- | ---------------------------------------------- |
| phpcs    | Lint PHP code                                  |
| phpcsfix | Lint and fix PHP code to follow the convention |

### Utils

| Command | Description       |
| ------- | ----------------- |
| cron    | Execute cron jobs |
