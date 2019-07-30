# ddTest.Uploader

Версия: 3.4

Опубликовано: 27-12-2018

Метки: Manager

Файл: [https://code.divandesign.biz/files/MODX/Uploader/ddTest.Uploader-3.4.zip](https://code.divandesign.biz/files/MODX/Uploader/ddTest.Uploader-3.4.zip)

Ссылка: [https://code.divandesign.biz/modx/uploader/3.4](http://code.divandesign.biz/modx/uploader/3.4)

## Описание 

### Краткое описание

Сниппет для вывода данных, разделённых через определённые разделители. Удобно использовать для вывода значений полей документов, сформированных виджетом [mm_ddMultipleFields](https://code.divandesign.biz/modx/mm_ddmultiplefields).

### Возможности

* Получение значения поля требуемого документа (TV) по его идентификатору. Параметры `inputString_docField` и `inputString_docId`.
* Возврат необходимого количества значений по значениям и номеру строки. Параметры `startRow`,` totalRows` и `filter`.
* Возврат необходимого значения по номеру столбца. Параметр `columns`.
* Сортировка строк (включая множественную сортировку) по значениям столбцов перед возвратом ('ASC', 'DESC', 'RAND', 'REVERSE'). Параметры `sortDir` и` sortBy`.
* Вывод данных, разделенных разделителями строк и столбцов. Параметры `rowGlue` и `colGlue`.
* Пустые значения удаляются перед выводом. Параметры `removeEmptyRows` и `removeEmptyCols`.
* Значения типографики перед выводом (используется сниппет ddTypograph). Параметр `typography`.
* Кодировать результирующий URL. Параметр `urlencode`.
* Кодировать результат в JSON. Параметр `outputFormat`.
* Возврат значений по заданным шаблонам (чанкам) строк и столбцов (также в шаблонах строк доступны плейсхолдеры `[+rowNumber+]` и `[+rowNumber.zeroBased+]` с номером строки). Параметры `rowTpl` и `colTpl`.
* Возврат результатов в чанке (параметр `outerTpl`). отправляющем дополнительные данные через плейсхолдеры (параметр `placeholders`)..

## Использует

* PHP >= 5.4.
* MODXEvo >= 1.1.
* MODXEvo.libraries.ddTools >= 0.18.
* MODXEvo.snippets.ddTypograph >= 1.4.3 (if typography is required).

## Снимки экрана

* ![image](http://code.divandesign.biz/images/modx/ddTest.Uploader/3_4/Screen1.png)
* ![image](http://code.divandesign.biz/images/modx/ddTest.Uploader/3_4/Screen2.png)

## Список изменений

+ Добавлена поддержка массивов для плейсхолдеров.
+ Добавлена поддержка формата JSON для параметра плейсхолдеров.
+ Добавлена поддержка формата JSON для параметра `inputString`.
* Следующие параметры были переименованы (фрагмент работает со старыми именами, но они устарели):
	* rowDelimiter → inputString_rowDelimiter.
	* colDelimiter → inputString_colDelimiter.
	
## Документация

###Installation

Элементы → Сниппеты: Создайте новый фрагмент со следующими данными:

* Имя сниппета: `ddTest.Uploader`.
* Описание: `&lt;b&gt;2.8&lt;/b&gt; Snippet gets the necessary document fields (and TV) by its id.`.
* Категория: `Core`.
* Анализировать DocBlock: `no`.
* Код сниппета (php): Вставить содержимое файла `ddTest.Uploader_snippet.php` из архива.

## Описание параметров

* $inputString {stirng_json|string_separated} — строка ввода, содержащая значения в формате JSON (https://en.wikipedia.org/wiki/JSON) или разделенные `$inputString_rowDelimiter` и `$inputString_colDelimiter`. @обязательно.
* $inputString_docField {string} — имя поля документа / TV, значение которого требуется получить. Если параметр передан, то входная строка будет взята из поля / TV и `inputString` будет игнорироваться. По умолчанию: —.
* $inputString_docId {integer} — идентификатор документа, значение поля / TV которого требуется получить. `inputString_docId` равно текущему идентификатору документа, поскольку `inputString_docId` не установлена. По умолчанию: —.
* $inputString_rowDelimiter {string|regexp} — Разделитель строк входной строки (если не `JSON`). По умолчанию: '||'.
* $inputString_colDelimiter {string|regexp} — Разделитель столбца входной строки (если не `JSON`). По умолчанию: '::'.
* $startRow {integer} — Индекс начальной строки (индексы начинаются с 0). По умолчанию: 0.
* $totalRows {integer|'all'} — максимальное количество возвращаемых строк. Все строки будут возвращены, если `totalRows` == 'all'. По умолчанию: 'all'.
* $columns {string_commaSeparated|'all'} — индексы возвращаемых столбцов (индексы начинаются с 0). Все столбцы будут возвращены, если `columns` == 'all'. По умолчанию: 'all'.
* $filter {string_separated} — Предложение фильтра для столбцов. Таким образом, '0::a||0::b||1::1' делает столбцы с 'a' или 'b' в столбце 0 и с 1 в столбце 1 для возврата. По умолчанию: ''.
* $removeEmptyRows {0|1} — требуется ли удалять пустые строки? По умолчанию: 1.
* $removeEmptyCols {0|1} — требуется ли удалять пустые столбцы? По умолчанию: 1.
* $sortBy {string_commaSeparated} — Индекс столбца для сортировки (индексы начинаются с 0). Параметр также принимает значения, разделенные запятыми, для множественной сортировки, например, '0,1'. По умолчанию: '0'.
* $sortDir {'ASC'|'DESC'|'RAND'|'REVERSE'|''} — направление сортировки строк. Строки будут возвращены в обратном порядке, если `sortDir` == 'REVERSE'. По умолчанию: ''.
* $typography {string_commaSeparated} — Разделенные запятыми индексы столбцов, значения которых должны быть исправлены (индексы начинаются с 0). Если не установлено, коррекция не будет. По умолчанию: —.
* $outputFormat {'html'|'JSON'|'array'|'htmlarray'} — Формат вывода результата. По умолчанию: 'HTML'.
* $rowGlue {string} — строка, объединяющая строки при рендеринге. Может использоваться вместе с `rowTpl`. По умолчанию: ''.
* $colGlue {string} — строка, которая объединяет столбцы при рендеринге. Он может использоваться вместе с `colTpl`, но не с `rowTpl` по понятным причинам. По умолчанию: ''.
* $rowTpl {string_chunkName|string} — шаблон для рендеринга строки (`outputFormat` должен быть == 'html'). Используйте встроенные шаблоны, начинающиеся с `@CODE:`. Доступные плейсхолдеры: `[+rowNumber+]` (индекс текущей строки, начинается с 1), `[+rowNumber.zeroBased+]` (индекс текущей строки, начинается с 0), `[+total+]` (общее количество строк ), `[+resultTotal+]` (общее количество возвращаемых строк), `[+col0+], [+col1+],…` (значения столбцов). По умолчанию: ''.
* $colTpl {string_commaSeparated_chunkName|string|'null'} — разделенный запятыми список шаблонов для рендеринга столбцов (`outputFormat` должен быть == 'html'). Используйте встроенные шаблоны, начинающиеся с `@CODE:`. Если число шаблонов меньше количества столбцов, то последний переданный шаблон будет использоваться для визуализации остальных столбцов. 'null' указывает рендеринг без шаблона. Доступные плейсхолдеры: `[+ val +]`, `[+ rowNumber +]` (индекс текущей строки, начинается с 1), `[+ rowNumber.zeroBased +]` (индекс текущей строки, начинается с 0). По умолчанию: ''.
* $outerTpl {string_chunkName|string} — шаблон оболочки (`outputFormat` должен быть != 'массив'). Используйте встроенные шаблоны, начинающиеся с `@CODE:`. Доступные заполнители: `[+result+]`, `[+total+]` (общее количество строк), `[+resultTotal+]` (общее количество возвращаемых строк), `[+rowY.colX+]` («Y» - номер строки, «X» - номер столбца). По умолчанию: ''.
* $placeholder {stirng_json|string_queryFormated} — дополнительные данные в виде JSON (https://en.wikipedia.org/wiki/JSON) или строки запроса (https://en.wikipedia.org/wiki/Query_string) должны быть переданы в `outerTpl`,` rowTpl` и `colTpl`. Например `{"pladeholder1":"value1", "pagetitle":"Мой классный заголовок страницы!"}` или `pladeholder1=value1&pagetitle=Мой классный заголовок страницы!`. Также поддерживаются массивы: `some[a]=one&some[b]=two`=>`[+some.a+]`, `[+some.b+]`; `some[]=one&some[]=two`=>`[+some.0+]`, `[some.1]`. По умолчанию: ''.
* $urlencode {0|1} — Требуется ли URL кодировать результат? `OutputFormat` должен быть! = `array`. Кодировка URL используется в соответствии с RFC 3986. По умолчанию: 0.
* $totalRowsToPlaceholder {string} — имя глобального заполнителя MODX, который содержит общее количество строк. Заполнитель не будет установлен, если значение totalRowsToPlaceholder пусто. По умолчанию: ''.
* $resultToPlaceholder {string} — имя глобального заполнителя MODX, который содержит результат фрагмента. Результат будет возвращаться обычным образом, если параметр пуст. По умолчанию: ''.

## Примеры

#### Вывод изображений с описаниями
Исходная строка (пусть находится в TV документа «images»):
`assets/images/some_img1.jpg::Изображение 1||assets/images/some_img2.jpg::Изображение 2`

Вызов сниппета в шаблоне документа:
```
[[ddGetMultipleField?
	&inputString=`[*images*]`
	&rowTpl=`images_item`
]]
```
Код чанка «images_item»:
`[+col1+]: &lt;img src="[+col0+]" alt="[+col1+]" /&gt;`

