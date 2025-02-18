# AjaxFormitLogin

Сниппет для вывода формы.

## Параметры

| Параметр                 | По умолчанию                                                          | Описание                                                                                                                                                                                                                                                                             |
|--------------------------|-----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **form**                 | aflExampleForm                                                        | Чанк формы                                                                                                                                                                                                                                                                           |
| **snippet**              | FormIt                                                                | Сниппет, который будет обрабатывать форму                                                                                                                                                                                                                                            |
| **hooks**                | FormItSaveForm,email                                                  | Хуки, которые будут использованы для обработки формы.                                                                                                                                                                                                                                |
| **emailTo**              |                                                                       | Email получателя                                                                                                                                                                                                                                                                     |
| **emailFrom**            |                                                                       | Email отправителя. При использовании SMTP нужно указывать email пользователя SMTP.                                                                                                                                                                                                   |
| **emailSubject**         |                                                                       | Тема письма.                                                                                                                                                                                                                                                                         |
| **emailTpl**             | aflExampleEmail                                                       | Чанк письма.                                                                                                                                                                                                                                                                         |
| **successMessage**       | Форма успешно отправлена! Менеджер свяжется с Вами в течение 5 минут. | Уведомление об успешной отправке формы.                                                                                                                                                                                                                                              |
| **clearFieldsOnSuccess** | 1                                                                     | Указывает JS очищать ли поля после отправки формы.                                                                                                                                                                                                                                   |
| **transmittedParams**    | ["success" => "", "error" => "aliases"]                               | Список параметров для передачи в JS.                                                                                                                                                                                                                                                 |
| **aliases**              | email==Email                                                          | Список псевдонимов полей для показа уведомлений об ошибках в них.                                                                                                                                                                                                                    |
| **validate**             | email:required:email                                                  | Список полей и их валидаторов.                                                                                                                                                                                                                                                       |
| **showUploadProgress**   | 1                                                                     | Указывает JS показывать ли процесс загрузки файлов.                                                                                                                                                                                                                                  |
| **spamProtection**       | 1                                                                     | Активирует встроенную защиту от спама.                                                                                                                                                                                                                                               |
| **redirectTimeout**      | 2000                                                                  | Задержка перед переадресацией в миллисекундах.                                                                                                                                                                                                                                       |
| **redirectTo**           |                                                                       | ID страницы переадресации или ссылка на страницу.                                                                                                                                                                                                                                    |
| **autoLogin**            |                                                                       | Авторизовывать ли пользователя автоматически после регистрации учётной записи.                                                                                                                                                                                                       |
| **passwordField**        | password                                                              | Имя поля содержащего пароль.                                                                                                                                                                                                                                                         |
| **usernameField**        | username                                                              | Имя поля содержащего имя пользователя.                                                                                                                                                                                                                                               |
| **activation**           |                                                                       | Нужна ли активация, если да - на email пользователя будет выслано письмо с ссылкой на страницу активации.                                                                                                                                                                            |
| **moderate**             |                                                                       | Нужна ли модерация. Если нужна - профиль пользователя будет заблокирован пока модератор его не разблокирует.                                                                                                                                                                         |
| **activationResourceId** |                                                                       | ID ресурса, на который будет отправлен пользователь для активации аккаунта.                                                                                                                                                                                                          |
| **usergroupsField**      |                                                                       | Поле со списком групп разделенных запятыми, в которые нужно добавить пользователя при регистрации. Можно указать так же уровень доступа (Member или SuperUser) и rank: group_id:pemission_id:rank, например `2:1:0`. Можно указать только два первых параметра или только ID группы. |
| **authenticateContexts** |                                                                       | Поле со списком контекстов разделенных запятыми, в которых нужно авторизовать пользователя.                                                                                                                                                                                          |
| **rememberme**           |                                                                       | Запоминать ли пользователя.                                                                                                                                                                                                                                                          |
| **activationUrlTime**    | 10800                                                                 | Время действия ссылки на активацию в секундах.                                                                                                                                                                                                                                       |
| **method**               |                                                                       | Метод класса AjaxIdentification (register, login, logout, forgot, update).                                                                                                                                                                                                           |

* вы так же можете использовать любые [параметры спиппета FormIt][1]

Как видно из таблицы по умолчанию сниппет настроен на отправку форм и сохранение их данных в админке.

## Пример использования

Минимальный вызов должен выглядеть так

```html
{'!AjaxFormitLogin' | snippet: [
'emailTo' => 'name@domain.ru',
'emailFrom' => 'noreply@domain.ru',
'emailSubject' => 'Тема письма'
]}
```

и обязательно должен вызываться некешированным. В чанк формы вы можете передавать какие угодно данные, указывая их как параметры сниппета. Так же любые данные можно
передавать в JS через параметр `transmittedParams`.
А оптимальный вызов такой:

```html
{'!AjaxFormitLogin' | snippet : [
'form' =>  'aflExampleForm',
'snippet' => 'FormIt',
'hooks' => 'FormItSaveForm,email',
'emailTo' => 'shev.art.v@yandex.ru',
'emailFrom' => 'noreply@art-sites.ru',
'emailSubject' => 'Тестовая форма',
'emailTpl' => 'aflExampleEmail',
'successMessage' => 'Форма успешно отправлена! Менеджер свяжется с Вами в течение 5 минут.',
'clearFieldsOnSuccess' => 1,
'transmittedParams' => ["success" => 'ym_goal', "error" => 'aliases'],
'aliases' => 'email==Email,phone==Телефон,name==Имя,politics==Правила сервиса',
'showUploadProgress' => 1,
'spamProtection' => 1,
'ym_goal' => 'TEST_GOAL',

'validate' => 'email:required:email,name:required:minLength=^3^,phone:required,politics:minValue=^1^',
'validationErrorMessage' => 'Исправьте, пожалуйста, ошибки!',
'email.vTextRequired' => 'Укажите email.',
'fullname.vTextRequired' => 'Укажите ФИО.',
'fullname.vTextMinLength' => 'Слишком короткое ФИО.',
'secret.vTextContains' => 'Кажется Вы робот. Если это не так, обновите страницу.',
'politics.vTextMinValue' => 'Примите наши условия.'
]}
```

[1]: https://docs.modx.com/current/ru/extras/formit
