# seoTabs

Сниппет для вывода SEOtabs на сайте.

## Параметры

| Параметр          | По умолчанию                                                     | Описание                                                                                                                                                                                                               |
| ----------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|**ajax**           | 0                                                                | Ajax загрузка данных таба
|**rid**            | 0                                                                | ID ресурса из которого брать табы. Если не указан, используется ID текущего ресурса.
|**up**             | 1                                                                | Искать табы у родителей если у текущего ресурса их нет.
|**css**            | null                                                             | Если вы хотите использовать собственные стили - укажите путь к ним здесь, или очистите параметр и загрузите их вручную через шаблон  сайта.
|**jquery**         | 0                                                                | Нужно ли подключать jQuery.
|**jqueryUrl**      | https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js | URL, подключаемой библиотеки jQuery.
|**js**             | {+assets_url}js/web/default.min.js                               | Если вы хотите использовать  собственные скрипты - укажите путь к ним здесь, или очистите параметр и  загрузите их вручную через шаблон сайта.
|**tpl**            | tpl.seoTabs                                                      | Чанк, для оформления результата работы сниппета.
|**tplTab**         | tpl.seoTabsTab                                                   | Чанк, для оформления таба.
|**tplTabContent**  | tpl.seoTabsContent                                               | Чанк, для оформления контента таба.
|**tplWrapper**     | tpl.seoTabsWrapper                                               | Чанк-обёртка, для обертывания всех результатов.

## Параметр AJAX

При присвоении параметра ajax значения «1» `(ajax => 1)`  в снипете seoTabs в коде виртуальных страниц SEO-табов не отображается содержимое остальных вкладок. При этом содержимое SEO-табов не содержится в коде основной страницы. Это позволяет создавать максимально уникальные виртуальные страницы для конкретных групп запросов.
