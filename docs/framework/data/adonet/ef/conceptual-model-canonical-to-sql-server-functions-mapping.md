---
title: Model koncepcyjny Canonical do mapowania funkcji serwera SQL
ms.date: 03/30/2017
ms.assetid: 1a2631bc-a426-4c0a-ba8d-26d9c80d39e2
ms.openlocfilehash: 3dd655e7acf924fa1bf0c09f0da82826e69482d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61606822"
---
# <a name="conceptual-model-canonical-to-sql-server-functions-mapping"></a>Model koncepcyjny Canonical do mapowania funkcji serwera SQL
W tym temacie opisano sposób koncepcyjny funkcje canonical modelu mapy z odpowiednimi funkcjami programu SQL Server.  
  
## <a name="date-and-time-functions"></a>Funkcje daty i godziny  
 W poniższej tabeli opisano funkcje date i time mapowania:  
  
|Funkcje Canonical|Funkcje programu SQL Server|  
|-------------------------|--------------------------|  
|[AddDays(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEADD(day, number, date)`|  
|[AddHours(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEADD(hour, number, date)`|  
|[AddMicroseconds(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEADD(microsecond, number, date)`|  
|[AddMilliseconds(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEADD(millisecond, number, date)`|  
|[AddMinutes(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEADD(minute, number, date)`|  
|[AddMonths(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEADD(month, number, date)`|  
|[AddNanoseconds(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEADD(nanosecond, number, date)`|  
|[AddSeconds(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEADD(second, number, date)`|  
|[AddYears(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEADD(year, number, date)`|  
|[CreateDateTime (rok, miesiąc, dzień, godzina, minuta, sekunda)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|Dla programu SQL Server 2000 i SQL Server 2005 `datetime` sformatowaną wartość zostanie utworzony na serwerze. Dla programu SQL Server 2008 i nowszych wersjach `datetime2` wartość zostanie utworzony na serwerze.|  
|[CreateDateTimeOffset (rok, miesiąc, dzień, godzinę, minuty, sekundy i tzoffset)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|A `datetimeoffset` sformatowaną wartość zostanie utworzony na serwerze.<br /><br /> Nie są obsługiwane w programie SQL Server 2000 lub SQL Server 2005.|  
|[CreateTime (godzina, minuta, sekunda)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|A `time` sformatowaną wartość zostanie utworzony na serwerze.<br /><br /> Nie są obsługiwane w programie SQL Server 2000 lub SQL Server 2005.|  
|[CurrentDateTime()](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`SysDateTime()` w SQLServer 2008.<br /><br /> `GetDate()` w SQLServer 2000 i SQLServer 2005.|  
|[CurrentDateTimeOffset()](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`SysDateTimeOffset()` w programie SQL Server 2008.<br /><br /> Nie są obsługiwane w programie SQL Server 2000 lub SQL Server 2005.|  
|[CurrentUtcDateTime()](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`SysUtcDateTime()` w SQLServer 2008. `GetUtcDate()` w programie SQL Server 2000 i SQL Server 2005.|  
|[DayOfYear(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DatePart(dayofyear, expression)`|  
|[Day(Expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DatePart(day, expression)`|  
|[DiffDays (startExpression, endExpression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(day, startdate, enddate)`|  
|[DiffHours (startExpression, endExpression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(hour, startdate, enddate)`|  
|[DiffMicroseconds (startExpression, endExpression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(microsecond, startdate, enddate)`|  
|[DiffMilliseconds(startExpression, endExpression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(millisecond, startdate, enddate)`|  
|[DiffMinutes (startExpression, endExpression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(minute, startdate, enddate)`|  
|[DiffNanoseconds (startExpression, endExpression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(nanosecond, startdate, enddate)`|  
|[DiffSeconds (startExpression, endExpression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(second, startdate, enddate)`|  
|[DiffYears (startExpression, endExpression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(year, startdate, enddate)`|  
|[GetTotalOffsetMinutes(DateTimeOffset)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DatePart(tzoffset, expression)`|  
|[Hour(Expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DatePart(hour, expression)`|  
|[Millisecond(Expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DatePart(millisecond, expression)`|  
|[MINUTE(Expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DatePart(minute, expression)`|  
|[Month(Expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DatePart(month, expression)`|  
|[Second(Expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DatePart(second, expression)`|  
|[Truncate(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|Dla programu SQL Server 2000 i SQL Server 2005, skróconą `datetime` sformatowaną wartość zostanie utworzony na serwerze. Dla programu SQL Server 2008 i nowsze wersje, skróconą `datetime2` lub `datetimeoffset` wartość zostanie utworzony na serwerze.|  
|[Year(Expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DatePart(YEAR, expression)`|  
  
## <a name="aggregate-functions"></a>Funkcje agregujące  
 W poniższej tabeli opisano funkcje agregujące mapowania:  
  
|Funkcje Canonical|Funkcje programu SQL Server|  
|-------------------------|--------------------------|  
|[Avg(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`AVG(expression)`|  
|[BigCount(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`BIGCOUNT(expression)`|  
|[Count(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`COUNT(expression)`|  
|[Min(Expression)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`MIN(expression)`|  
|[MAX(Expression)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`MAX(expression)`|  
|[StDev(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`STDEV(expression)`|  
|[StDevP(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`STDEVP(expression)`|  
|[Sum(Expression)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`SUM(expression)`|  
|[Var(Expression)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`VAR(expression)`|  
|[VarP(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`VARP(expression)`|  
  
## <a name="math-functions"></a>Funkcje matematyczne  
 W poniższej tabeli opisano funkcje matematyczne mapowania:  
  
|Funkcje Canonical|Funkcje programu SQL Server|  
|-------------------------|--------------------------|  
|[ABS(Value)](../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)|`ABS(value)`|  
|[CEILING(Value)](../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)|`CEILING(value)`|  
|[FLOOR(Value)](../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)|`FLOOR(value)`|  
|[Power(Value)](../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)|`POWER(value, exponent)`|  
|[ROUND(Value)](../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)|`ROUND(value, digits, 0)`|  
|[Obetnij](../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)|`ROUND(value , digits, 1)`|  
  
## <a name="string-functions"></a>Funkcje ciągów  
 W poniższej tabeli opisano funkcje ciągów mapowania:  
  
|Funkcje Canonical|Funkcje programu SQL Server|  
|-------------------------|--------------------------|  
|[Contains(String, TARGET)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`CHARINDEX(target, string)`|  
|[Concat (ciąg1, ciąg2)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|ciąg1 + ciąg2|  
|[EndsWith (string, docelowy)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`CHARINDEX(REVERSE(target), REVERSE(string)) = 1`<br /><br /> **Uwaga** `CHARINDEX` funkcja zwraca `false` Jeśli `string` znajduje się w kolumnie o stałej długości ciągu i `target` jest stałą. W tym przypadku cały ciąg jest przeszukiwany, włączając wszelkie dopełnienie spacje końcowe. Możliwym obejściem jest przycięte dane w ciągu o stałej długości przed przekazaniem ciąg `EndsWith` funkcji, jak w poniższym przykładzie: `EndsWith(TRIM(string), target)`|  
|[IndexOf (docelowy, ciąg2)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`CHARINDEX(target, string2)`|  
|[Po lewej stronie (ciąg1, długość)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`LEFT(string1, length)`|  
|[Długość (ciąg)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`LEN(string)`|  
|[LTrim(string)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`LTRIM(string)`|  
|[Po prawej stronie (ciąg1, długość)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`RIGHT (string1, length)`|  
|[TRIM(String)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`LTRIM(RTRIM(string))`|  
|[Zastąp (ciąg1, ciąg2 ciąg3)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`REPLACE(string1, string2, string3)`|  
|[Reverse (ciąg)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`REVERSE (string)`|  
|[RTrim(string)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`RTRIM(string)`|  
|[StartsWith (string, docelowy)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`CHARINDEX(target, string)`|  
|[Substring (ciąg, początek, długość)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`SUBSTRING(string, start, length)`|  
|[ToLower(string)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`LOWER(string)`|  
|[ToUpper(string)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`UPPER(string)`|  
  
## <a name="bitwise-functions"></a>Funkcje bitowe  
 W poniższej tabeli opisano funkcje bitowe mapowania:  
  
|Funkcje Canonical|Funkcje programu SQL Server|  
|-------------------------|--------------------------|  
|[BitWiseAnd (wartość1, wartość2)](../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)|Wartość1 & wartość2|  
|[BitWiseNot (wartość)](../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)|~ wartość|  
|[BitWiseOr (wartość1, wartość2)](../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)|value1 &#124; value2|  
|[BitWiseXor (wartość1, wartość2)](../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)|Wartość1 ^ wartość2|
