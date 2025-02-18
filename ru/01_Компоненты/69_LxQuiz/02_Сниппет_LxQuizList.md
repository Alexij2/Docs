## LxQuizList

Вызывается без кеширования! Отображает список доступных тестов с возможностью фильтровать каждый из тестов при помощи плагина на событие `lxqBeforeListQuiz`

### Параметры

`quizIds (необязательный)`

ID тестов через запятую. В случае, если указано, то выходной результат будет отсортирован в точном соответствии с последовательностью идентификаторов quizIds

`tpl (необязательный)`

чанк вывода (с использованием pdoFetch и fenom)

По-умолчанию: `lxQuizListTpl`

`errorTpl (необязательный)`

По умолчанию: `lxQuizListTpl`

`where (необязательный)`

Аналог where для pdoTools

`limit (необязательный)`

Аналог limit для pdoTools

`quizPageId (необязательный)`

ID страницы, на которой будет отображаться тест (там, где установлен сниппет lxQuiz без параметра quizId). В случае, если не указан, будет взята текущая страница.

### События

#### lxqBeforeListQuiz

Для того чтобы исключить отображение тестирования из списка, необходимо в плагине, реагирующем на событие `lxqBeforeListQuiz`, добавить непустое значение в `$modx->event->_ouput`.

Может использоваться, например, для сокрытия сданных тестов для текущего пользователя, или для сокрытия тестов, проходить которые текущий пользователь по каким-либо причинам не имеет права.

Пример плагина:

```php
/**
 * Скрывает из списка тестирование с ID = 1
 * @var lxqQuiz $quiz
 */

$modx->event->_output = $quiz && $quiz->id == 1;
return;
```
