# back-end

#### Prison Admin Schema
| field    | data type        | metadata                                            |
| :------- | :--------------- | :-------------------------------------------------- |
| id       | unsigned integer | primary key, auto-increments, generated by database |
| username | string           | required, unique                                    |
| password | string           | required, unique                                    |

#### Prisoner Profile Schema
| field       | data type        | metadata                                                             |
| :---------- | :--------------- | :------------------------------------------------------------------- |
| id          | unsigned integer | primary key, auto-increments, generated by database                  |
| prison_id   | unsigned integer | foreign key referencing id in Prison table, generated by the database|
| name        | string           | required                                                             |
| can leave   | boolean          | required                                                             |

#### Skills Schema
| field       | data type        | metadata                                                             |
| :---------- | :--------------- | :------------------------------------------------------------------- |
| id          | unsigned integer | primary key, auto-increments, generated by database                  |
| prisoner_id | unsigned integer | foreign key referencing id in Prison table, generated by the database|
| description | string           | required                                                             |

#### Previous Experience Schema
| field       | data type        | metadata                                                             |
| :---------- | :--------------- | :------------------------------------------------------------------- |
| id          | unsigned integer | primary key, auto-increments, generated by database                  |
| prisoner_id | unsigned integer | foreign key referencing id in Prison table, generated by the database|
| description | string           | required                                                             |
| date        | string           | required                                                             |

### Prison Schema
| field       | data type        | metadata                                                             |
| :---------- | :--------------- | :------------------------------------------------------------------- |
| id          | unsigned integer | primary key, auto-increments, generated by database                  |
| name        | string           | required, string, unique                                             |
| address     | string           | required, string, unique                                             |
| prisoner qty| string           | required                                                             |

### Endpoints
Base URL: `
`
| Request Method | Endpoint             | Description                                                           |
| :------------- | :------------------- | :-------------------------------------------------------------------- |
| `POST`         | `/auth/login`        | Logs an admin in and returns a token                                  |
| `POST`         | `/auth/register`     | creates a prison admin                                                |
| `POST`         | `/prison`            | adds a prison profile                                                 |
| `POST`         |`/prison/:id/prisoners| adds a prisoner to a prison                                           |
| `GET`          | `/prisons`           | returns all prisons                                                   |
| `GET`          | `/prisons/:id/prisoners`   | returns all prisoners for a particular prison                   |
| `GET`          | `/prisons/:id/prisoners/:id`| returns a particular prisoner profile                          |


| `GET`          | `/users/usersinfo`   | returns user information for all users                                |
| `GET`          | `/users/:id/info`    | returns user information for a given user                             |
| `PUT`          | `/users/:id/entry`   | updates a journal entry. :id refers to the entry id                   |
| `PUT`          | `/users/:id/info`    | updates user information. :id refers to the info id                   |
| `Delete`       | `/users/:id/entry`   | deletes a journal entry. :id refers to the entry id                   |
| `Delete`       | `/users/:id/info`    | deletes a users info entry. :id refers to the info id                 |
| `Delete`       | `/users/:id/`        | deletes a user. :id refers to the users id                            |