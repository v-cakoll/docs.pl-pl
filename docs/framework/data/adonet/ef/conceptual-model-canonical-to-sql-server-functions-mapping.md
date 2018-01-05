---
title: Model koncepcyjny Canonical do mapowania funkcji serwera SQL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a2631bc-a426-4c0a-ba8d-26d9c80d39e2
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ad42c31353851f0846a484f7ab8bcb83c71d0e0b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="conceptual-model-canonical-to-sql-server-functions-mapping"></a>Model koncepcyjny Canonical do mapowania funkcji serwera SQL
W tym temacie opisano sposób koncepcyjny modelu funkcji kanonicznej mapę, aby odpowiednie funkcje programu SQL Server.  
  
## <a name="date-and-time-functions"></a>Funkcje daty i godziny  
 W poniższej tabeli opisano funkcje daty i godziny mapowania:  
  
|Canonical funkcji|Funkcje programu SQL Server|  
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
|[CreateDateTime (roku, miesiąc, dzień, godzinę, minutę, sekundę)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|Dla programu SQL Server 2000 i SQL Server 2005 `datetime` sformatowana wartość jest tworzona na serwerze. Dla programu SQL Server 2008 i nowszych wersjach `datetime2` wartość jest tworzona na serwerze.|  
|[CreateDateTimeOffset (roku, miesiąc, dzień, godzinę, minutę, sekundę, tzoffset)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|A `datetimeoffset` sformatowana wartość jest tworzona na serwerze.<br /><br /> Nie są obsługiwane w programie SQL Server 2000 lub SQL Server 2005.|  
|[CreateTime (godzina, minuty, sekundy)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|A `time` sformatowana wartość jest tworzona na serwerze.<br /><br /> Nie są obsługiwane w programie SQL Server 2000 lub SQL Server 2005.|  
|[CurrentDateTime()](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`SysDateTime()`2008 SQLServer.<br /><br /> `GetDate()`w przypadku SQLServer 2000 i SQL 2005.|  
|[CurrentDateTimeOffset()](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`SysDateTimeOffset()`w programie SQL Server 2008.<br /><br /> Nie są obsługiwane w programie SQL Server 2000 lub SQL Server 2005.|  
|[CurrentUtcDateTime()](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`SysUtcDateTime()`2008 SQLServer. `GetUtcDate()`w programie SQL Server 2000 i SQL Server 2005.|  
|[DayOfYear(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DatePart(dayofyear, expression)`|  
|[Day(Expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DatePart(day, expression)`|  
|[DiffDays (startExpression, endExpression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(day, startdate, enddate)`|  
|[DiffHours (startExpression, endExpression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(hour, startdate, enddate)`|  
|[DiffMicroseconds (startExpression, endExpression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(microsecond, startdate, enddate)`|  
|[DiffMilliseconds (startExpression, endExpression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DATEDIFF(millisecond, startdate, enddate)`|  
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
|[TRUNCATE(Expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|Dla programu SQL Server 2000 i SQL Server 2005, skróconą `datetime` sformatowana wartość jest tworzona na serwerze. Dla programu SQL Server 2008 i nowszych wersji, skróconą `datetime2` lub `datetimeoffset` wartość jest tworzona na serwerze.|  
|[Year(Expression)](../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)|`DatePart(YEAR, expression)`|  
  
## <a name="aggregate-functions"></a>Funkcje agregujące  
 W poniższej tabeli opisano funkcje agregujące mapowania:  
  
|Canonical funkcji|Funkcje programu SQL Server|  
|-------------------------|--------------------------|  
|[AVG(Expression)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`AVG(expression)`|  
|[BigCount(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`BIGCOUNT(expression)`|  
|[Count(Expression)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`COUNT(expression)`|  
|[Min(Expression)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`MIN(expression)`|  
|[MAX(Expression)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`MAX(expression)`|  
|[StDev(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`STDEV(expression)`|  
|[StDevP(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`STDEVP(expression)`|  
|[Sum(Expression)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`SUM(expression)`|  
|[Var(Expression)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`VAR(expression)`|  
|[VarP(expression)](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)|`VARP(expression)`|  
  
## <a name="math-functions"></a>Funkcje matematyczne  
 W poniższej tabeli opisano funkcje matematyczne mapowania:  
  
|Canonical funkcji|Funkcje programu SQL Server|  
|-------------------------|--------------------------|  
|[ABS(Value)](../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)|`ABS(value)`|  
|[CEILING(Value)](../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)|`CEILING(value)`|  
|[FLOOR(Value)](../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)|`FLOOR(value)`|  
|[Power(Value)](../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)|`POWER(value, exponent)`|  
|[ROUND(Value)](../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)|`ROUND(value, digits, 0)`|  
|[TRUNCATE](../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)|`ROUND(value , digits, 1)`|  
  
## <a name="string-functions"></a>Funkcje ciągów  
 W poniższej tabeli opisano funkcje ciągów mapowania:  
  
|Canonical funkcji|Funkcje programu SQL Server|  
|-------------------------|--------------------------|  
|[Contains(String, TARGET)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`CHARINDEX(target, string)`|  
|[Concat (ciąg1, ciąg2)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|ciąg1 + ciąg2|  
|[EndsWith (string, docelowy)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`CHARINDEX(REVERSE(target), REVERSE(string)) = 1`<br /><br /> **Uwaga** `CHARINDEX` funkcja zwraca `false` Jeśli `string` jest przechowywany w kolumnie ciągu o stałej długości i `target` jest stałą. W takim przypadku cały ciąg będzie przeszukiwana, w tym wszelkie uzupełnienia spacje końcowe. Możliwym obejściem jest przyciąć danych w ciągu o stałej długości przed przekazaniem ciąg `EndsWith` funkcji, jak w poniższym przykładzie:`EndsWith(TRIM(string), target)`|  
|[IndexOf (docelowej, ciąg2)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`CHARINDEX(target, string2)`|  
|[LEFT (ciąg1, długość)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`LEFT(string1, length)`|  
|[Długość (ciąg)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`LEN(string)`|  
|[LTrim(string)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`LTRIM(string)`|  
|[RIGHT (ciąg1, długość)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`RIGHT (string1, length)`|  
|[TRIM(String)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`LTRIM(RTRIM(string))`|  
|[Zastąp (ciąg1, ciąg2, ciąg3)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`REPLACE(string1, string2, string3)`|  
|[Reverse (ciąg)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`REVERSE (string)`|  
|[RTrim(string)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`RTRIM(string)`|  
|[StartsWith (string, docelowy)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`CHARINDEX(target, string)`|  
|[Substring (ciąg, początek, długość)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`SUBSTRING(string, start, length)`|  
|[ToLower(string)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`LOWER(string)`|  
|[ToUpper(string)](../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)|`UPPER(string)`|  
  
## <a name="bitwise-functions"></a>Funkcje bitowe  
 W poniższej tabeli opisano funkcje bitowe mapowania:  
  
|Canonical funkcji|Funkcje programu SQL Server|  
|-------------------------|--------------------------|  
|[BitWiseAnd (wartość1, wartość2)](../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)|Wartość1 & wartość2|  
|[BitWiseNot (wartość)](../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)|~ wartość|  
|[BitWiseOr (wartość1, wartość2)](../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)|Wartość1 &#124; wartość2|  
|[BitWiseXor (wartość1, wartość2)](../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)|Wartość1 ^ wartość2|
