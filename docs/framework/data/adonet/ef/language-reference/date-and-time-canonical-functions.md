---
title: Funkcji daty i godziny Canonical
ms.date: 03/30/2017
ms.assetid: 9628b74f-1585-436a-b385-8b02ed0cdd63
ms.openlocfilehash: 3dd6c0da3f9851df7bb9725d9d6c08fef5a0d3d3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251096"
---
# <a name="date-and-time-canonical-functions"></a>Funkcji daty i godziny Canonical
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]obejmuje funkcje kanoniczne daty i godziny.  
  
## <a name="remarks"></a>Uwagi  
 W poniższej tabeli przedstawiono funkcje kanoniczne daty [!INCLUDE[esql](../../../../../../includes/esql-md.md)] i godziny. `datetime`<xref:System.DateTime> jest wartością.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|`AddNanoseconds(expression,number)`|Dodaje określoną `number` liczbę nanosekund `expression`do.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, lub `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.|  
|`AddMicroseconds(expression,number)`|Dodaje określone `number` mikrosekundy `expression`do.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, lub `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.|  
|`AddMilliseconds(expression,number)`|Dodaje określoną `number` liczbę milisekund `expression`do.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, lub `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.|  
|`AddSeconds(expression,number)`|Dodaje określoną `number` liczbę sekund `expression`do.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, lub `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.|  
|`AddMinutes(expression,number)`|Dodaje określoną `number` liczbę minut `expression`do.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, lub `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.|  
|`AddHours(expression,number)`|Dodaje określoną `number` liczbę godzin `expression`do.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, lub `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.|  
|`AddDays(expression,number)`|Dodaje określoną `number` liczbę dni `expression`do.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime` lub `DateTimeOffset`.<br /><br /> `number`: `Int32`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.|  
|`AddMonths(expression,number)`|Dodaje określoną `number` liczbę miesięcy `expression`do.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime` lub `DateTimeOffset`.<br /><br /> `number`: `Int32`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.|  
|`AddYears(expression,number)`|Dodaje określone `number` lata `expression`do.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime` lub `DateTimeOffset`.<br /><br /> `number`: `Int32`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.|  
|`CreateDateTime(year,month,day,hour,minute,second)`|Zwraca nową `DateTime` wartość jako bieżącą datę i godzinę serwera w strefie czasowej serwera.<br /><br /> **Argumenty**<br /><br /> `year`, `month` ,`day`, ,`minute`: i`Int16` . `hour` `Int32`<br /><br /> `second`: `Double`.<br /><br /> **Wartość zwracana**<br /><br /> A `DateTime`.|  
|`CreateDateTimeOffset(year,month,day,hour,minute,second,tzoffset)`|Zwraca nową `DateTimeOffset` wartość jako bieżącą datę i godzinę serwera względem uniwersalnego czasu koordynowanego (UTC).<br /><br /> **Argumenty**<br /><br /> `year`, `month`, `day`, `hour`, `minute`, `tzoffset`: `Int32`.<br /><br /> `second`: `Double`.<br /><br /> **Wartość zwracana**<br /><br /> A `DateTimeOffset`.|  
|`CreateTime(hour,minute,second)`|Zwraca nową `Time` wartość jako bieżącą godzinę.<br /><br /> **Argumenty**<br /><br /> `hour`i `minute`: `Int32`.<br /><br /> `second`: `Double`.<br /><br /> **Wartość zwracana**<br /><br /> A `Time`.|  
|`CurrentDateTime()`|`DateTime` Zwraca wartość jako bieżącą datę i godzinę serwera w strefie czasowej serwera.<br /><br /> **Wartość zwracana**<br /><br /> A `DateTime`.|  
|`CurrentDateTimeOffset()`|Zwraca bieżącą datę, godzinę i przesunięcie jako `DateTimeOffset`.<br /><br /> **Wartość zwracana**<br /><br /> A `DateTimeOffset`.|  
|`CurrentUtcDateTime()`|<xref:System.DateTime> Zwraca wartość jako bieżącą datę i godzinę serwera w strefie czasowej UTS.<br /><br /> **Wartość zwracana**<br /><br /> A `DateTime`.|  
|`Day(expression)`|Zwraca część dnia z `expression` `Int32` zakresu od 1 do 31.<br /><br /> **Argumenty**<br /><br /> A `DateTime` i `DateTimeOffset`.<br /><br /> **Wartość zwracana**<br /><br /> A `Int32`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns 12.`<br /><br /> `Day(cast('03/12/1998' as DateTime))`|  
|`DayOfYear(expression)`|Zwraca część dnia z `expression` `Int32` przedziału od 1 do 366, gdzie 366 jest zwracany przez ostatni dzień roku przestępnego.<br /><br /> **Argumenty**<br /><br /> A `DateTime` lub `DateTimeOffset`.<br /><br /> **Wartość zwracana**<br /><br /> A `Int32`.|  
|`DiffNanoseconds(startExpression,endExpression)`|Zwraca różnicę w nanosekundach, między `startExpression` i. `endExpression`<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime`, lub`DateTimeOffset`. `Time` **Uwaga:** `startExpression` i`endExpression` musi być tego samego typu. <br /><br /> **Wartość zwracana**<br /><br /> A `Int32`.|  
|`DiffMilliseconds(startExpression,endExpression)`|Zwraca różnicę (w milisekundach) między `startExpression` i `endExpression`.<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime`, lub`DateTimeOffset`. `Time` **Uwaga:** `startExpression` i`endExpression` musi być tego samego typu. <br /><br /> **Wartość zwracana**<br /><br /> A `Int32`.|  
|`DiffMicroseconds(startExpression,endExpression)`|Zwraca różnicę, w mikrosekundach, między `startExpression` i. `endExpression`<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime`, lub`DateTimeOffset`. `Time` **Uwaga:** `startExpression` i`endExpression` musi być tego samego typu. <br /><br /> **Wartość zwracana**<br /><br /> A `Int32`.|  
|`DiffSeconds(startExpression,endExpression)`|Zwraca różnicę (w sekundach) między `startExpression` i. `endExpression`<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime`, lub`DateTimeOffset`. `Time` **Uwaga:** `startExpression` i`endExpression` musi być tego samego typu. <br /><br /> **Wartość zwracana**<br /><br /> A `Int32`.|  
|`DiffMinutes(startExpression,endExpression)`|Zwraca różnicę (w minutach) między `startExpression` i. `endExpression`<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime`, lub`DateTimeOffset`. `Time` **Uwaga:** `startExpression` i`endExpression` musi być tego samego typu. <br /><br /> **Wartość zwracana**<br /><br /> A `Int32`.|  
|`DiffHours(startExpression,endExpression)`|Zwraca różnicę (w godzinach) między `startExpression` i. `endExpression`<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime`, lub`DateTimeOffset`. `Time` **Uwaga:** `startExpression` i`endExpression` musi być tego samego typu. <br /><br /> **Wartość zwracana**<br /><br /> A `Int32`.|  
|`DiffDays(startExpression,endExpression)`|Zwraca różnicę (w dniach) między `startExpression` i. `endExpression`<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime` lub .`DateTimeOffset` **Uwaga:** `startExpression` i`endExpression` musi być tego samego typu. <br /><br /> **Wartość zwracana**<br /><br /> A `Int32`.|  
|`DiffMonths(startExpression,endExpression)`|Zwraca różnicę w miesiącach, między `startExpression` i. `endExpression`<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime` lub .`DateTimeOffset` **Uwaga:** `startExpression` i`endExpression` musi być tego samego typu. <br /><br /> **Wartość zwracana**<br /><br /> A `Int32`.|  
|`DiffYears(startExpression,endExpression)`|Zwraca różnicę (w latach) między `startExpression` i. `endExpression`<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime` lub .`DateTimeOffset` **Uwaga:** `startExpression` i`endExpression` musi być tego samego typu. <br /><br /> **Wartość zwracana**<br /><br /> A `Int32`.|  
|`GetTotalOffsetMinutes(datetimeoffset)`|Zwraca liczbę minut, przez jaką `datetimeoffset` jest przesunięty od GMT. Zwykle jest to między + 780 i – 780 (+ lub-13 godzin). **Uwaga:**  Ta funkcja jest obsługiwana tylko w SQL Server 2008. <br /><br /> **Argumenty**<br /><br /> A `DateTimeOffset`.<br /><br /> **Wartość zwracana**<br /><br /> A `Int32`.|  
|`Hour(expression)`|Zwraca część godziny z `expression` `Int32` przedziału od 0 do 23.<br /><br /> **Argumenty**<br /><br /> A `DateTime, Time` i `DateTimeOffset`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns 22.`<br /><br /> `Hour(cast('22:35:5' as DateTime))`|  
|`Millisecond(expression)`|Zwraca część milisekundową z `expression` `Int32` przedziału od 0 do 999.<br /><br /> **Argumenty**<br /><br /> A `DateTime, Time` i `DateTimeOffset`.<br /><br /> **Wartość zwracana**<br /><br /> A `Int32`.|  
|`Minute(expression)`|Zwraca część minuty z `expression` `Int32` przedziału od 0 do 59.<br /><br /> **Argumenty**<br /><br /> A `DateTime, Time` lub `DateTimeOffset`.<br /><br /> **Wartość zwracana**<br /><br /> A `Int32`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns 35`<br /><br /> `Minute(cast('22:35:5' as DateTime))`|  
|`Month(expression)`|Zwraca część miesiąca z `expression` `Int32` przedziału od 1 do 12.<br /><br /> **Argumenty**<br /><br /> A `DateTime` lub `DateTimeOffset`.<br /><br /> **Wartość zwracana**<br /><br /> A `Int32`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns 3.`<br /><br /> `Month(cast('03/12/1998' as DateTime))`|  
|`Second(expression)`|Zwraca część sekund z `expression` `Int32` przedziału od 0 do 59.<br /><br /> **Argumenty**<br /><br /> A `DateTime, Time` i `DateTimeOffset`.<br /><br /> **Wartość zwracana**<br /><br /> A `Int32`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns 5`<br /><br /> `Second(cast('22:35:5' as DateTime))`|  
|`TruncateTime(expression)`|Zwraca wartość `expression`, która obcina wartości czasu.<br /><br /> **Argumenty**<br /><br /> A `DateTime` lub `DateTimeOffset`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.|  
|`Year(expression)`|Zwraca część `expression` roku `Int32` jako.`YYYY`<br /><br /> **Argumenty**<br /><br /> A `DateTime` i `DateTimeOffset`.<br /><br /> **Wartość zwracana**<br /><br /> A `Int32`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns 1998.`<br /><br /> `Year(cast('03/12/1998' as DateTime))`|  
  
 Te funkcje zostaną zwrócone `null` , jeśli `null` dane wejściowe.  
  
 Równoważne funkcje są dostępne w dostawcy zarządzanym przez klienta programu Microsoft SQL. Aby uzyskać więcej informacji, zobacz temat [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Zobacz także

- [Funkcje Canonical](canonical-functions.md)
