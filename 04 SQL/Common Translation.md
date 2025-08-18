| 🔑 Keyword in Question            | 🛠 SQL Tool / Pattern                                                              |
| --------------------------------- | ---------------------------------------------------------------------------------- |
| **“More than one”**               | `GROUP BY col HAVING COUNT(*) > 1`                                                 |
| **“Exactly one / unique”**        | `GROUP BY col HAVING COUNT(*) = 1`                                                 |
| **“At least N”**                  | `GROUP BY col HAVING COUNT(*) >= N`                                                |
| **“Duplicates”**                  | same as “more than one”                                                            |
| **“Latest / most recent”**        | `MAX(date)` OR `ROW_NUMBER() OVER(PARTITION BY id ORDER BY date DESC)`             |
| **“Earliest”**                    | `MIN(date)` OR order ascending                                                     |
| **“Previous value”**              | `LAG(value) OVER(PARTITION BY id ORDER BY date)`                                   |
| **“Next value”**                  | `LEAD(value) OVER(PARTITION BY id ORDER BY date)`                                  |
| **“Running total”**               | `SUM(value) OVER(ORDER BY date)`                                                   |
| **“Cumulative count”**            | `COUNT(*) OVER(ORDER BY date)`                                                     |
| **“Percentage of total”**         | `COUNT(*) * 1.0 / SUM(COUNT(*)) OVER()`                                            |
| **“Top N”**                       | Use `ROW_NUMBER() OVER(PARTITION BY group ORDER BY score DESC)` then filter `<= N` |
| **“Rank” (with ties)**            | `RANK()`                                                                           |
| **“Dense rank”**                  | `DENSE_RANK()`                                                                     |
| **“Exists in another table”**     | `WHERE EXISTS (SELECT 1 FROM B WHERE B.col = A.col)`                               |
| **“Does not exist”**              | `NOT EXISTS` OR `LEFT JOIN … WHERE other.id IS NULL`                               |
| **“Match all”**                   | `HAVING COUNT(DISTINCT col) = <expected>`                                          |
| **“Unique combination”**          | `GROUP BY col1, col2 HAVING COUNT(*) = 1`                                          |
| **“Never / did not”**             | `LEFT JOIN … WHERE right.id IS NULL`                                               |
| **“Consecutive days / sessions”** | `LAG()` with `DATEDIFF()`                                                          |
| **“Highest / lowest in group”**   | `ROW_NUMBER() OVER(PARTITION BY … ORDER BY … DESC/ASC)`                            |
