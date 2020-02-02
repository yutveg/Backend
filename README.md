# back-end

### Endpoints For Login / Registration

| Request Method | Endpoint         | Description                          |
| :------------- | :--------------- | :----------------------------------- |
| `POST`         | `/auth/login`    | Logs an admin in and returns a token |
| `POST`         | `/auth/register` | creates a prison admin               |

### Endpoints For Prisons

| Request Method | Endpoint       | Description                                         |
| :------------- | :------------- | :-------------------------------------------------- |
| `POST`         | `/prisons`     | adds a prison profile                               |
| `GET`          | `/prisons`     | returns all prisons                                 |
| `DEL`          | `/prisons/:id` | deletes a prison (and all prisoners in that prison) |
| `PUT`          | `/prisons/:id` | updates a prison's information                      |

### Endpoints For Prisoners

| Request Method | Endpoint                     | Description                                                              |
| :------------- | :--------------------------- | :----------------------------------------------------------------------- |
| `POST`         | `/prison/:id/prisoners`      | adds a prisoner to a prison                                              |
| `GET`          | `/prisons/:id/prisoners`     | returns all prisoners for a prison, their name, availability, and skills |
| `GET`          | `/prisons/:id/prisoners/:id` | returns a prisoner by id, their basic info, skills, and experience       |
| `DEL`          | `/prisons/:id/prisoners/:id` | deletes a prisoner                                                       |
| `PUT`          | `/prisons/:id/prisoners/:id` | updates a prisoner's basic information (name, availability)              |

### Endpoints For Prisoner Skills

| Request Method | Endpoint                            | Description                |
| :------------- | :---------------------------------- | :------------------------- |
| `POST`         | `/prisons/:id/prisoners/:id/skills` | adds a prisoner's skill    |
| `DEL`          | `/prisons/:id/prisoners/:id/skills` | deletes a prisoner's skill |
| `PUT`          | `/prisons/:id/prisoners/:id/skills` | updates a prisoner's skill |

### Endpoints For Prisoner Experience

| Request Method | Endpoint                                | Description                            |
| :------------- | :-------------------------------------- | :------------------------------------- |
| `POST`         | `/prisons/:id/prisoners/:id/experience` | adds prisoner's previous experience    |
| `DEL`          | `/prisons/:id/prisoners/:id/experience` | deletes prisoner's previous experience |
| `PUT`          | `/prisons/:id/prisoners/:id/experience` | updates prisoner's previous experience |

#### Prison Admin Schema

| field    | data type        | metadata                                            |
| :------- | :--------------- | :-------------------------------------------------- |
| id       | unsigned integer | primary key, auto-increments, generated by database |
| username | string           | required, unique                                    |
| password | string           | required, unique                                    |

#### Prisoner Profile Schema

| field     | data type        | metadata                                                              |
| :-------- | :--------------- | :-------------------------------------------------------------------- |
| id        | unsigned integer | primary key, auto-increments, generated by database                   |
| prison_id | unsigned integer | foreign key referencing id in Prison table, generated by the database |
| name      | string           | required                                                              |
| can leave | boolean          | required                                                              |

#### Skills Schema

| field       | data type        | metadata                                            |
| :---------- | :--------------- | :-------------------------------------------------- |
| id          | unsigned integer | primary key, auto-increments, generated by database |
| prisoner_id | unsigned integer | foreign key referencing id in prisoner table        |
| description | string           | required                                            |

#### Previous Experience Schema

| field       | data type        | metadata                                            |
| :---------- | :--------------- | :-------------------------------------------------- |
| id          | unsigned integer | primary key, auto-increments, generated by database |
| prisoner_id | unsigned integer | foreign key referencing id in prisoner table        |
| description | string           | required                                            |
| date        | string           | required                                            |

### Prison Schema

| field             | data type        | metadata                                            |
| :---------------- | :--------------- | :-------------------------------------------------- |
| id                | unsigned integer | primary key, auto-increments, generated by database |
| name              | string           | required, string, unique                            |
| address           | string           | required, string, unique                            |
| zipcode           | integer          | required, integer                                   |
| prisoner_quantity | integer          | not required, nullable                              |
