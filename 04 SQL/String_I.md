| Function / Pattern                        | Purpose                     | Example / Usage                                        | Notes                                        |
| ----------------------------------------- | --------------------------- | ------------------------------------------------------ | -------------------------------------------- |
| `CONCAT(s1,s2,...)`                       | Concatenate strings         | `CONCAT(first_name,' ',last_name)`                     | Standard string concat                       |
| `CONCAT_WS(sep,s1,s2,...)`                | Concatenate with separator  | `CONCAT_WS('-', '2025','08','19') → '2025-08-19'`      | WS = with separator                          |
| `SUBSTRING(str,pos,len)`                  | Extract substring           | `SUBSTRING('abcdef',2,3) → 'bcd'`                      | MySQL also supports `SUBSTR`                 |
| `LEFT(str,n)` / `RIGHT(str,n)`            | First/last n chars          | `LEFT('abcdef',3) → 'abc'`                             | Often used for date parsing                  |
| `TRIM(str)`                               | Remove spaces               | `TRIM(' abc ') → 'abc'`                                | Also `LTRIM` / `RTRIM`                       |
| `REPLACE(str, from, to)`                  | Replace substring           | `REPLACE('abcabc','a','x') → 'xbcxbc'`                 | Useful for cleaning data                     |
| `LOWER(str)` / `UPPER(str)`               | Case conversion             | `LOWER('ABC') → 'abc'`                                 | Often used in joins or comparisons           |
| `LENGTH(str)` / `CHAR_LENGTH(str)`        | String length               | `LENGTH('abc') → 3`                                    | Counting characters                          |
| `LIKE`                                    | Simple pattern match        | `name LIKE 'J%n' → John, Jason`                        | `%`=any string, `_`=single char              |
| `REGEXP` / `RLIKE`                        | Regex match                 | `name REGEXP '^J.*n$' → John`                          | Powerful for complex matching                |
| `REGEXP_REPLACE(str, pattern, repl)`      | Replace using regex         | `REGEXP_REPLACE('abc123','[0-9]','X') → 'abcXXX'`      | MySQL 8+                                     |
| `REGEXP_SUBSTR(str, pattern)`             | Extract regex match         | `REGEXP_SUBSTR('abc123','[0-9]+') → '123'`             | MySQL 8+                                     |
| `INSTR(str,substr)`                       | Find substring position     | `INSTR('abcdef','cd') → 3`                             |                                              |
| `LOCATE(substr,str,pos)`                  | Same as INSTR               | `LOCATE('cd','abcdef') → 3`                            | pos = optional start                         |
| `POSITION(substr IN str)`                 | Standard SQL                | `POSITION('cd' IN 'abcdef') → 3`                       | ANSI SQL                                     |
| `LPAD(str,len,pad)` / `RPAD(str,len,pad)` | Pad string                  | `LPAD('5',3,'0') → '005'`                              | Good for IDs or date parts                   |
| `SPLIT(str,delim)`                        | Split string to array       | `SPLIT('a,b,c',',') → ['a','b','c']`                   | MySQL 8+ / other engines                     |
| `JSON_TABLE(...)`                         | Convert JSON array to table | `JSON_TABLE('[1,2,3]','$[*]' COLUMNS(x INT PATH '$'))` | Useful for splitting lists                   |
| `CASE WHEN ... THEN ... END`              | Conditional string          | `CASE WHEN salary>50000 THEN 'High' ELSE 'Low' END`    | Often used in LeetCode string categorization |
| `COUNT(CASE WHEN condition THEN 1 END)`   | Conditional count           | `COUNT(CASE WHEN rating<3 THEN 1 END)`                 | Counting specific patterns                   |
| `ROUND(expr, decimals)`                   | Round numeric results       | `ROUND(AVG(amount),2)`                                 | Often needed for percentages                 |
