# ddTest.Uploader

Version: 3.4

Published: 27-12-2018

Tags: Manager

File: [https://code.divandesign.biz/files/MODX/Uploader/ddTest.Uploader-3.4.zip](https://code.divandesign.biz/files/MODX/Uploader/ddTest.Uploader-3.4.zip)

Link: [https://code.divandesign.biz/modx/Uploader/3.4](http://code.divandesign.biz/modx/Uploader/3.4)

## Description 

### Summary

Snippet for outputting data separated by defined delimiters. It is convenient to use to display the field values of documents formed by the widget. [mm_ddMultipleFields](https://code.divandesign.biz/modx/mm_ddmultiplefields).

### Features

* Field value getting of a required document (TV) by its id. `inputString_docField` and `inputString_docId` parameters.
* Return of a required values number by values and row number. `startRow`, `totalRows` and `filter` parameters.
* Return of a required value by columns number. The `columns` paramter.
* Rows sorting (including multiple sorting) by columns values before returning (`ASC`, `DESC`, `RAND`, `REVERSE`). `sortDir` и `sortBy` parameters.
* Output of data being separated by rows and columns delimeters. `rowGlue` and `colGlue` parameters.
* Empty values remove before output. `removeEmptyRows` and `removeEmptyCols` parameters.
* Values typography before output (the snippet ddTypograph is used). The `typography` parameter.
* Result URL encode. The `urlencode` parameter.
* Result JSON encode. The `outputFormat` parameter.
* Values returning by the given templates (chunks) of rows and columns (also the `[+rowNumber+]` and `[+rowNumber.zeroBased+]` placeholders with a  row number is available in the row templates). `rowTpl` и `colTpl` parameters.
* Returning results in a wrapper chunk (the `outerTpl` parameter). 
* Sending additional data through placeholders (the `placeholders` parameter).

## Uses

* PHP >= 5.4.
* MODXEvo >= 1.1.
* MODXEvo.libraries.ddTools >= 0.18.
* MODXEvo.snippets.ddTypograph >= 1.4.3 (if typography is required).


## Screenshots

* ![image](http://code.divandesign.biz/images/modx/ddTest.Uploader/3_4/Screen1.png)
* ![image](http://code.divandesign.biz/images/modx/ddTest.Uploader/3_4/Screen2.png)

## Changelog

+ Arrays support for placeholders were added.
+ Added JSON format support for the placeholders parameter.
+ Added JSON format support for the inputString parameter.
* The following parameters were renamed (the snippet works with the old names but they are deprecated):
	* rowDelimiter → inputString_rowDelimiter.
	* colDelimiter → inputString_colDelimiter.
	
## Documentation
###Installation
Elements → Snippets: Create a new snippet with the following data:

* Snippet name: `ddTest.Uploader`.
* Description: `&lt;b&gt;2.8&lt;/b&gt; Snippet gets the necessary document fields (and TV) by its id.`.
* Category: `Core`.
* Parse DocBlock: `no`.
* Snippet code (php): Insert content of the `ddTest.Uploader_snippet.php` file from the archive.

## Parameters description

* $inputString {stirng_json|string_separated} — The input string containing values in JSON (https://en.wikipedia.org/wiki/JSON) or separated by `$inputString_rowDelimiter` and `$inputString_colDelimiter`. @required
* $inputString_docField {string} — The name of the document field/TV which value is required to get. If the parameter is passed then the input string will be taken from the field/TV and `inputString` will be ignored. Default: —.
* $inputString_docId {integer} — ID of the document which field/TV value is required to get. `inputString_docId` equals the current document id since `inputString_docId` is unset. Default: —.
* $inputString_rowDelimiter {string|regexp} — The input string row delimiter (if not `JSON`). Default: '||'.
* $inputString_colDelimiter {string|regexp} — The input string column delimiter (if not `JSON`). Default: '::'.
* $startRow {integer} — The index of the initial row (indexes start at 0). Default: 0.
* $totalRows {integer|'all'} — The maximum number of rows to return. All rows will be returned if `totalRows` == 'all'. Default: 'all'.
* $columns {string_commaSeparated|'all'} — The indexes of columns to return (indexes start at 0). All columns will be returned if `columns` == 'all'. Default: 'all'.
* $filter {string_separated} — Filter clause for columns. Thus, '0::a||0::b||1::1' makes the columns with either 'a' or 'b' in the 0 column and with 1 in the 1 column to be returned. Default: ''.
* $removeEmptyRows {0|1} — Is it required to remove empty rows? Default: 1.
* $removeEmptyCols {0|1} — Is it required to remove empty columns? Default: 1.
* $sortBy {string_commaSeparated} — The index of the column to sort by (indexes start at 0). The parameter also takes comma-separated values for multiple sort, e.g. '0,1'. Default: '0'.
* $sortDir {'ASC'|'DESC'|'RAND'|'REVERSE'|''} — Rows sorting direction. The rows will be returned in reversed order if `sortDir` == 'REVERSE'. Default: ''.
* $typography {string_commaSeparated} — The comma separated indexes of the columns which values have to be corrected (indexes start at 0). If unset, there will be no correction. Default: —.
* $outputFormat {'html'|'JSON'|'array'|'htmlarray'} — Result output format. Default: 'html'.
* $rowGlue {string} — The string that combines rows while rendering. It can be used along with “rowTpl”. Default: ''.
* $colGlue {string} — The string that combines columns while rendering. It can be used along with `colTpl`, but not with `rowTpl` for obvious reasons. Default: ''.
* $rowTpl {string_chunkName|string} — The template for row rendering (`outputFormat` has to be == 'html'). Use inline templates starting with `@CODE:`. Available placeholders: `[+rowNumber+]` (index of current row, starts at 1), `[+rowNumber.zeroBased+]` (index of current row, starts at 0), `[+total+]` (total number of rows), `[+resultTotal+]` (total number of returned rows), `[+col0+],[+col1+],…` (column values). Default: ''.
* $colTpl {string_commaSeparated_chunkName|string|'null'} — The comma-separated list of templates for column rendering (`outputFormat` has to be == 'html'). Use inline templates starting with `@CODE:`. If the number of templates is lesser than the number of columns then the last passed template will be used to render the rest of the columns. 'null' specifies rendering without a template. Available placeholders: `[+val+]`, `[+rowNumber+]` (index of current row, starts at 1), `[+rowNumber.zeroBased+]` (index of current row, starts at 0). Default: ''.
* $outerTpl {string_chunkName|string} — Wrapper template (`outputFormat` has to be != 'array'). Use inline templates starting with `@CODE:`. Available placeholders: `[+result+]`, `[+total+]` (total number of rows), `[+resultTotal+]` (total number of returned rows), `[+rowY.colX+]` (“Y” — row number, “X” — column number). Default: ''.
* $placeholders {stirng_json|string_queryFormated} — Additional data as JSON (https://en.wikipedia.org/wiki/JSON) or Query string (https://en.wikipedia.org/wiki/Query_string) has to be passed into `outerTpl`, `rowTpl` and `colTpl`. E. g. `{"pladeholder1": "value1", "pagetitle": "My awesome pagetitle!"}` or `pladeholder1=value1&pagetitle=My awesome pagetitle!`. Arrays are supported too: `some[a]=one&some[b]=two` => `[+some.a+]`, `[+some.b+]`; `some[]=one&some[]=two` => `[+some.0+]`, `[some.1]`. Default: ''.
* $urlencode {0|1} — Is it required to URL encode the result? “outputFormat” has to be != 'array'. URL encoding is used according to RFC 3986. Default: 0.
* $totalRowsToPlaceholder {string} — The name of the global MODX placeholder that holds the total number of rows. The placeholder won't be set if `totalRowsToPlaceholder` is empty. Default: ''.
* $resultToPlaceholder {string} — The name of the global MODX placeholder that holds the snippet result. The result will be returned in a regular manner if the parameter is empty. Default: ''.

## Examples

#### Display images with descriptions
Source line (let it be in the “images” TV document):
`assets/images/some_img1.jpg::Изображение 1||assets/images/some_img2.jpg::Изображение 2`

Call snippet in document template:
```
[[ddGetMultipleField?
	&inputString=`[*images*]`
	&rowTpl=`images_item`
]]
```
Chunk code for "images_item"::
`[+col1+]: &lt;img src="[+col0+]" alt="[+col1+]" /&gt;`

