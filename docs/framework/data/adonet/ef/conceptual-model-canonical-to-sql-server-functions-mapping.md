---
title: Model koncepcyjny Canonical do mapowania funkcji serwera SQL
ms.date: 03/30/2017
ms.assetid: 1a2631bc-a426-4c0a-ba8d-26d9c80d39e2
ms.openlocfilehash: f997fbf39f3dee07cc0d58a39fca779f55236606
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251681"
---
# <a name="conceptual-model-canonical-to-sql-server-functions-mapping"></a>Model koncepcyjny Canonical do mapowania funkcji serwera SQL
W tym temacie opisano sposób, w jaki funkcje kanoniczne modelu koncepcyjnego są mapowane na odpowiednie funkcje SQL Server.  
  
## <a name="date-and-time-functions"></a>Funkcje daty i godziny  
 W poniższej tabeli opisano mapowanie funkcji daty i godziny:  
  
|Funkcje kanoniczne|Funkcje SQL Server|  
|-------------------------|--------------------------|  
|[AddDays (wyrażenie)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(day, number, date)`|  
|[AddHours (wyrażenie)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(hour, number, date)`|  
|[AddMicroseconds (wyrażenie)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(microsecond, number, date)`|  
|[AddMilliseconds(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(millisecond, number, date)`|  
|[Addminut (wyrażenie)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(minute, number, date)`|  
|[Addmiesiącach (wyrażenie)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(month, number, date)`|  
|[AddNanoseconds(expression)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(nanosecond, number, date)`|  
|[AddSeconds (wyrażenie)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(second, number, date)`|  
|[AddYears (wyrażenie)](./language-reference/date-and-time-canonical-functions.md)|`DATEADD(year, number, date)`|  
|[Xmldatetime (rok, miesiąc, dzień, godzina, minuta, sekunda)](./language-reference/date-and-time-canonical-functions.md)|W przypadku SQL Server 2000 i SQL Server 2005 `datetime` na serwerze zostanie utworzona sformatowana wartość. W przypadku SQL Server 2008 i nowszych wersji `datetime2` na serwerze zostanie utworzona wartość.|  
|[Xmldatetimeoffset (Year, month, Day, Hour, minute, Second, TZoffset)](./language-reference/date-and-time-canonical-functions.md)|Na serwerze zostanie utworzona sformatowanawartość.`datetimeoffset`<br /><br /> Nieobsługiwane w SQL Server 2000 lub SQL Server 2005.|  
|[Czas trwania (godzina, minuta, sekunda)](./language-reference/date-and-time-canonical-functions.md)|Na serwerze zostanie utworzona sformatowanawartość.`time`<br /><br /> Nieobsługiwane w SQL Server 2000 lub SQL Server 2005.|  
|[CurrentDateTime()](./language-reference/date-and-time-canonical-functions.md)|`SysDateTime()`w programie SQLServer 2008.<br /><br /> `GetDate()`w przypadku programu SQLServer 2000 i SQLServer 2005.|  
|[CurrentDateTimeOffset()](./language-reference/date-and-time-canonical-functions.md)|`SysDateTimeOffset()`w SQL Server 2008.<br /><br /> Nieobsługiwane w SQL Server 2000 lub SQL Server 2005.|  
|[CurrentUtcDateTime()](./language-reference/date-and-time-canonical-functions.md)|`SysUtcDateTime()`w programie SQLServer 2008. `GetUtcDate()`w SQL Server 2000 i SQL Server 2005.|  
|[Dzieńroku (wyrażenie)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(dayofyear, expression)`|  
|[Dzień (wyrażenie)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(day, expression)`|  
|[DiffDays(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(day, startdate, enddate)`|  
|[DiffHours(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(hour, startdate, enddate)`|  
|[DiffMicroseconds(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(microsecond, startdate, enddate)`|  
|[DiffMilliseconds(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(millisecond, startdate, enddate)`|  
|[DiffMinutes(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(minute, startdate, enddate)`|  
|[DiffNanoseconds(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(nanosecond, startdate, enddate)`|  
|[DiffSeconds(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(second, startdate, enddate)`|  
|[DiffYears(startExpression, endExpression)](./language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(year, startdate, enddate)`|  
|[GetTotalOffsetMinutes(DateTimeOffset)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(tzoffset, expression)`|  
|[Hour (wyrażenie)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(hour, expression)`|  
|[Milisekundy (wyrażenie)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(millisecond, expression)`|  
|[Minuta (wyrażenie)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(minute, expression)`|  
|[Miesiąc (wyrażenie)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(month, expression)`|  
|[Second (wyrażenie)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(second, expression)`|  
|[Truncate(expression)](./language-reference/date-and-time-canonical-functions.md)|W przypadku SQL Server 2000 i SQL Server 2005 zostanie utworzona `datetime` skrócona wartość sformatowana na serwerze. W przypadku SQL Server 2008 i nowszych wersji na serwerze `datetime2` zostanie `datetimeoffset` utworzona obcięta lub wartość.|  
|[Year (wyrażenie)](./language-reference/date-and-time-canonical-functions.md)|`DatePart(YEAR, expression)`|  
  
## <a name="aggregate-functions"></a>Funkcje agregujące  
 W poniższej tabeli opisano mapowanie funkcji agregujących:  
  
|Funkcje kanoniczne|Funkcje SQL Server|  
|-------------------------|--------------------------|  
|[Avg(expression)](./language-reference/aggregate-canonical-functions.md)|`AVG(expression)`|  
|[BigCount(expression)](./language-reference/aggregate-canonical-functions.md)|`BIGCOUNT(expression)`|  
|[Count (wyrażenie)](./language-reference/aggregate-canonical-functions.md)|`COUNT(expression)`|  
|[Min (wyrażenie)](./language-reference/aggregate-canonical-functions.md)|`MIN(expression)`|  
|[Max (wyrażenie)](./language-reference/aggregate-canonical-functions.md)|`MAX(expression)`|  
|[StDev (wyrażenie)](./language-reference/aggregate-canonical-functions.md)|`STDEV(expression)`|  
|[StDevP (wyrażenie)](./language-reference/aggregate-canonical-functions.md)|`STDEVP(expression)`|  
|[Sum (wyrażenie)](./language-reference/aggregate-canonical-functions.md)|`SUM(expression)`|  
|[Var (wyrażenie)](./language-reference/aggregate-canonical-functions.md)|`VAR(expression)`|  
|[VarP (wyrażenie)](./language-reference/aggregate-canonical-functions.md)|`VARP(expression)`|  
  
## <a name="math-functions"></a>Funkcje matematyczne  
 W poniższej tabeli opisano mapowanie funkcji matematycznych:  
  
|Funkcje kanoniczne|Funkcje SQL Server|  
|-------------------------|--------------------------|  
|[ABS (wartość)](./language-reference/math-canonical-functions.md)|`ABS(value)`|  
|[Górny limit (wartość)](./language-reference/math-canonical-functions.md)|`CEILING(value)`|  
|[Piętro (wartość)](./language-reference/math-canonical-functions.md)|`FLOOR(value)`|  
|[Moc (wartość)](./language-reference/math-canonical-functions.md)|`POWER(value, exponent)`|  
|[Round (wartość)](./language-reference/math-canonical-functions.md)|`ROUND(value, digits, 0)`|  
|[Obciąć](./language-reference/math-canonical-functions.md)|`ROUND(value , digits, 1)`|  
  
## <a name="string-functions"></a>Funkcje ciągów  
 W poniższej tabeli opisano mapowanie funkcji ciągów:  
  
|Funkcje kanoniczne|Funkcje SQL Server|  
|-------------------------|--------------------------|  
|[Zawiera (ciąg, cel)](./language-reference/string-canonical-functions.md)|`CHARINDEX(target, string)`|  
|[Concat (ciąg1, ciąg2)](./language-reference/string-canonical-functions.md)|ciąg1 + ciąg2|  
|[EndsWith (ciąg, obiekt docelowy)](./language-reference/string-canonical-functions.md)|`CHARINDEX(REVERSE(target), REVERSE(string)) = 1`<br /><br /> **Uwaga** Funkcja zwraca wartość `false` `target` , `string` jeśli jest przechowywana w kolumnie ciągu o stałej długości i jest stałą. `CHARINDEX` W takim przypadku przeszukiwany jest cały ciąg, w tym wszystkie spacje końcowe uzupełniania. Możliwe obejście polega na przycięciu danych w ciągu o stałej długości przed przekazaniem ciągu do `EndsWith` funkcji, jak w poniższym przykładzie:`EndsWith(TRIM(string), target)`|  
|[IndexOf (target, ciąg2)](./language-reference/string-canonical-functions.md)|`CHARINDEX(target, string2)`|  
|[Left (ciąg1, długość)](./language-reference/string-canonical-functions.md)|`LEFT(string1, length)`|  
|[Długość (ciąg)](./language-reference/string-canonical-functions.md)|`LEN(string)`|  
|[LTrim (ciąg)](./language-reference/string-canonical-functions.md)|`LTRIM(string)`|  
|[Right (ciąg1, długość)](./language-reference/string-canonical-functions.md)|`RIGHT (string1, length)`|  
|[Trim (ciąg)](./language-reference/string-canonical-functions.md)|`LTRIM(RTRIM(string))`|  
|[Zastąp (ciąg1, ciąg2, string3)](./language-reference/string-canonical-functions.md)|`REPLACE(string1, string2, string3)`|  
|[Odwróć (ciąg)](./language-reference/string-canonical-functions.md)|`REVERSE (string)`|  
|[RTrim(string)](./language-reference/string-canonical-functions.md)|`RTRIM(string)`|  
|[StartsWith (ciąg, obiekt docelowy)](./language-reference/string-canonical-functions.md)|`CHARINDEX(target, string)`|  
|[Podciąg (ciąg, początek, długość)](./language-reference/string-canonical-functions.md)|`SUBSTRING(string, start, length)`|  
|[ToLower (ciąg)](./language-reference/string-canonical-functions.md)|`LOWER(string)`|  
|[ToUpper (ciąg)](./language-reference/string-canonical-functions.md)|`UPPER(string)`|  
  
## <a name="bitwise-functions"></a>Funkcje bitowe  
 W poniższej tabeli opisano mapowanie funkcji bitowych:  
  
|Funkcje kanoniczne|Funkcje SQL Server|  
|-------------------------|--------------------------|  
|[BitWiseAnd (wartość1, wartość2)](./language-reference/bitwise-canonical-functions.md)|wartość1 & wartość2|  
|[BitWiseNot (wartość)](./language-reference/bitwise-canonical-functions.md)|~ wartość|  
|[Bitowy (wartość1, wartość2)](./language-reference/bitwise-canonical-functions.md)|wartość1 &#124; wartość2|  
|[BitWiseXor (wartość1, wartość2)](./language-reference/bitwise-canonical-functions.md)|Wartość1 ^ wartość2|
