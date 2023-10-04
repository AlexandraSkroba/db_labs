Скроба Александра Павлновна 153504 <br>
Тема разрабатываемого проета "Издательская платформа"

# Функциональные требования
<ul> 
<li>Авторизация пользователя</li>
<li>Управление пользователями (CRUD)</li>
<li>Система ролей (Гость, Пользователь, Админ)</li>
<li>Журналирование  действий пользователя</li>
</ul>

<b>Незарегистрированный пользователь может: </b>
1. Читать статьи и комментарии
2. Просматривать информацию в профиле у дргих авторизированных пользователей
3. Регистрироваться, указывая свои данные

<b>Неавторизованный пользователь может: </b>
1. Читать статьи и комментарии
2. Просматривать информацию в профиле у дргих авторизированных пользователей
3. Войти в ситсему, указывая свои данные

<b>Авторизированный пользоатель может:</b>
1. Читать статьи и комментарии
2. Просматривать информацию в профиле у дргих авторизированных пользователей
3. Управлять своими статьями (CRUD)
4. Управлять своими комментариями (CRUD)
5. Добавлять статьи в избранное
6. Оставлять реакцию на комментарии и статьи
7. Получать уведомления
8. Редактировать данные профиля

<b>Админ должен уметь:</b>
1. Управлять пользователями(CRUD)
2. Управлять статьями(CRUD)
3. Управлять комментариями(CRUD)
4. Управлять категориями статей (CRUD)

# Список таблиц
<h3>User</h3>
<ul>
  <li>Поля</li>
  <ul>
    <li>id (Primary Key, INT, AUTOINCREMENT)</li>
    <li>username (VARCHAR(50))</li>
    <li>email (VARCHAR(255))</li>
    <li>password (VARCHAR(50))</li>
    <li>role_id (Foreign Key, INT, связь с roles)</li>
  </ul>
  <li>Связи</li>
  <ul>
    <li>Один к одному с таблицей profile</li>
    <li>Один ко многим с таблицей user_activity</li>
    <li>Один ко многим с таблицей notifications</li>
    <li>Один ко многим с таблицей articles</li>
    <li>Один ко многим с таблицей comments</li>
    <li>Один ко многим с таблицей ratings</li>
    <li>Многие к одному с таблицей roles</li>
    <li>Многие ко многим с таблицей articles посредством таблицы favorites</li>
  </ul>
</ul>

<h3>Profile</h3>
<ul>
  <li>Поля</li>
  <ul>
    <li>id (Primary Key, INT, AUTOINCREMENT)</li>
    <li>user_id (Foreign Key, INT, связь с user)</li>
    <li>name (VARCHAR(50))</li>
    <li>biography (text?)</li>
    <li>date_of_birth (date?)</li>
    <li>gender (enum?)</li>
    <li>links (text?)</li>
  </ul>
  <li>Связи</li>
  <ul>
    <li>Один к одному с таблицей user</li>
    <li>Один к одному с таблицей images</li>
  </ul>
</ul>

<h3>User_activity</h3>
<ul>
  <li>Поля</li>
  <ul>
    <li>id (Primary Key, INT, AUTOINCREMENT)</li>
    <li>user_id (Foreign Key, INT, связь с user)</li>
    <li>activity_type (VARCHAR(255))</li>
    <li>date (timestamp)</li>
  </ul>
  <li>Связи</li>
  <ul>
    <li>Многие к одному с таблицей user</li>
  </ul>
</ul>

<h3>Roles</h3>
<ul>
  <li>Поля</li>
  <ul>
    <li>id (Primary Key, INT, AUTOINCREMENT)</li>
    <li>role_name (VARCHAR(255))</li>
  </ul>
  <li>Связи</li>
  <ul>
    <li>Один ко многим с таблицей user</li>
  </ul>
</ul>

<h3>Notifications</h3>
<ul>
  <li>Поля</li>
  <ul>
    <li>id (Primary Key, INT, AUTOINCREMENT)</li>
    <li>user_id (Foreign Key, INT, связь с user)</li>
    <li>notification_text (text)</li>
  </ul>
  <li>Связи</li>
  <ul>
    <li>Многие ко одному с таблицей user</li>
  </ul>
</ul>

<h3>Images</h3>
<ul>
  <li>Поля</li>
  <ul>
    <li>id (Primary Key, INT, AUTOINCREMENT)</li>
    <li>image_url (text)</li>
    <li>article_id (Foreign Key, INT, связь с articles)</li>
    <li>profile_id (Foreign Key, INT, связь с profile)</li>
  </ul>
  <li>Связи</li>
  <ul>
    <li>Один ко одному с таблицей profile</li>
    <li>Многие ко одному с таблицей articles</li>
  </ul>
</ul>

<h3>Ratings</h3>
<ul>
  <li>Поля</li>
  <ul>
    <li>id (Primary Key, INT, AUTOINCREMENT)</li>
    <li>user_id (Foreign Key, INT, связь с user)</li>
    <li>article_id (Foreign Key, INT?, связь с articles)</li>
    <li>comment_id (Foreign Key, INT?, связь с comments)</li>
  </ul>
  <li>Связи</li>
  <ul>
    <li>Многие ко одному с таблицей user</li>
    <li>Многие ко одному с таблицей user</li>
    <li>Многие ко одному с таблицей articles</li>
  </ul>
</ul>

<h3>Comments</h3>
<ul>
  <li>Поля</li>
  <ul>
    <li>id (Primary Key, INT, AUTOINCREMENT)</li>
    <li>user_id (Foreign Key, INT, связь с user)</li>
    <li>article_id (Foreign Key, INT, связь с articles)</li>
    <li>comment_text (VARCHAR(200))</li>
    <li>comment_date (timestamp)</li>
  </ul>
  <li>Связи</li>
  <ul>
    <li>Один ко многим с таблицей rating</li>
    <li>Многие ко одному с таблицей user</li>
    <li>Многие ко одному с таблицей articles</li>
  </ul>
</ul>

<h3>Articles</h3>
<ul>
  <li>Поля</li>
  <ul>
    <li>id (Primary Key, INT, AUTOINCREMENT)</li>
    <li>author_id (Foreign Key, INT, связь с user)</li>
    <li>title (VARCHAR(200))</li>
    <li>content (text)</li>
    <li>published_at (timestamp)</li>
  </ul>
  <li>Связи</li>
  <ul>
    <li>Один ко многим с таблицей images</li>
    <li>Один ко многим с таблицей ratings</li>
    <li>Один ко многим с таблицей comments</li>
    <li>Многие ко многим с таблицей categories посредством таблицы article_category</li>
    <li>Многие ко многим с таблицей tags посредством таблицы articles_tags</li>
    <li>Многие ко многим с таблицей user посредством таблицы favorites</li>
  </ul>
</ul>

<h3>Categories</h3>
<ul>
  <li>Поля</li>
  <ul>
    <li>id (Primary Key, INT, AUTOINCREMENT)</li>
    <li>category_name (VARCHAR(50))</li>
  </ul>
  <li>Связи</li>
  <ul>
    <li>Многие ко многим с таблицей articles посредством таблицы article_category</li>
  </ul>
</ul>

<h3>Tags</h3>
<ul>
  <li>Поля</li>
  <ul>
    <li>id (Primary Key, INT, AUTOINCREMENT)</li>
    <li>tag_name (VARCHAR(50))</li>
  </ul>
  <li>Связи</li>
  <ul>
    <li>Многие ко многим с таблицей articles посредством таблицы article_tags</li>
  </ul>
</ul>
