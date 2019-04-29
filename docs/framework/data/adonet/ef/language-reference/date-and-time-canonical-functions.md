---
title: Funkcji daty i godziny Canonical
ms.date: 03/30/2017
ms.assetid: 9628b74f-1585-436a-b385-8b02ed0cdd63
ms.openlocfilehash: 1e54fa3d763fa08d7bafd9b002f0458ec3a6293d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61606013"
---
# <a name="date-and-time-canonical-functions"></a>Funkcji daty i godziny Canonical
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] obejmuje funkcje canonical daty i godziny.  
  
## <a name="remarks"></a>Uwagi  
 W poniższej tabeli przedstawiono daty i godziny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] funkcje canonical. `datetime` jest <xref:System.DateTime> wartość.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|`AddNanoseconds(expression,number)`|Dodaje określony `number` z nanosekundach do `expression`.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, lub `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.|  
|`AddMicroseconds(expression,number)`|Dodaje określony `number` mikrosekund do `expression`.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, lub `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.|  
|`AddMilliseconds(expression,number)`|Dodaje określony `number` milisekund do `expression`.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, lub `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.|  
|`AddSeconds(expression,number)`|Dodaje określony `number` czasu w sekundach `expression`.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, lub `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.|  
|`AddMinutes(expression,number)`|Dodaje określony `number` minut `expression`.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, lub `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.|  
|`AddHours(expression,number)`|Dodaje określony `number` godziny `expression`.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, lub `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.|  
|`AddDays(expression,number)`|Dodaje określony `number` dni do `expression`.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime` lub `DateTimeOffset`.<br /><br /> `number`: `Int32`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.|  
|`AddMonths(expression,number)`|Dodaje określony `number` miesięcy do `expression`.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime` lub `DateTimeOffset`.<br /><br /> `number`: `Int32`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.|  
|`AddYears(expression,number)`|Dodaje określony `number` lat do `expression`.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime` lub `DateTimeOffset`.<br /><br /> `number`: `Int32`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.|  
|`CreateDateTime(year,month,day,hour,minute,second)`|Zwraca nowy `DateTime` wartości bieżącej daty i czasu serwera w strefie czasowej serwera.<br /><br /> **Argumenty**<br /><br /> `year`, `month`, `day`, `hour`, `minute`: `Int16` i `Int32`.<br /><br /> `second`: `Double`.<br /><br /> **Wartość zwracana**<br /><br /> A `DateTime`.|  
|`CreateDateTimeOffset(year,month,day,hour,minute,second,tzoffset)`|Zwraca nowy `DateTimeOffset` wartości bieżącej daty i czasu serwera względem uniwersalnego czasu koordynowanego (UTC).<br /><br /> **Argumenty**<br /><br /> `year`, `month`, `day`, `hour`, `minute`, `tzoffset`: `Int32`.<br /><br /> `second`: `Double`.<br /><br /> **Wartość zwracana**<br /><br /> A `DateTimeOffset`.|  
|`CreateTime(hour,minute,second)`|Zwraca nowy `Time` wartość jako bieżący czas.<br /><br /> **Argumenty**<br /><br /> `hour` i `minute`: `Int32`.<br /><br /> `second`: `Double`.<br /><br /> **Wartość zwracana**<br /><br /> A `Time`.|  
|`CurrentDateTime()`|Zwraca `DateTime` wartości bieżącej daty i czasu serwera w strefie czasowej serwera.<br /><br /> **Wartość zwracana**<br /><br /> A `DateTime`.|  
|`CurrentDateTimeOffset()`|Zwraca bieżącą datę, czas i przesunięcie jako `DateTimeOffset`.<br /><br /> **Wartość zwracana**<br /><br /> A `DateTimeOffset`.|  
|`CurrentUtcDateTime()`|Zwraca <xref:System.DateTime> wartości bieżącej daty i czasu serwera w strefie czasowej UTS.<br /><br /> **Wartość zwracana**<br /><br /> A `DateTime`.|  
|`Day(expression)`|Zwraca część dotyczącą dnia z `expression` jako `Int32` od 1 do 31.<br /><br /> **Argumenty**<br /><br /> A `DateTime` i `DateTimeOffset`.<br /><br /> **Wartość zwracana**<br /><br /> `Int32`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns 12.`<br /><br /> `Day(cast('03/12/1998' as DateTime))`|  
|`DayOfYear(expression)`|Zwraca część dotyczącą dnia z `expression` jako `Int32` od 1 do 366, gdy 366 jest zwracany w ciągu ostatniego dnia w roku przestępnym.<br /><br /> **Argumenty**<br /><br /> A `DateTime` lub `DateTimeOffset`.<br /><br /> **Wartość zwracana**<br /><br /> `Int32`.|  
|`DiffNanoseconds(startExpression,endExpression)`|Zwraca w nanosekundach różnicę między `startExpression` i `endExpression`.<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime`, `DateTimeOffset`, lub `Time`. **Uwaga:** `startExpression` i `endExpression` muszą być tego samego typu. <br /><br /> **Wartość zwracana**<br /><br /> `Int32`.|  
|`DiffMilliseconds(startExpression,endExpression)`|Zwraca różnicę, w milisekundach między `startExpression` i `endExpression`.<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime`, `DateTimeOffset`, lub `Time`. **Uwaga:** `startExpression` i `endExpression` muszą być tego samego typu. <br /><br /> **Wartość zwracana**<br /><br /> `Int32`.|  
|`DiffMicroseconds(startExpression,endExpression)`|Zwraca w mikrosekundach, różnicę między `startExpression` i `endExpression`.<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime`, `DateTimeOffset`, lub `Time`. **Uwaga:** `startExpression` i `endExpression` muszą być tego samego typu. <br /><br /> **Wartość zwracana**<br /><br /> `Int32`.|  
|`DiffSeconds(startExpression,endExpression)`|Zwraca różnicę w sekundach między `startExpression` i `endExpression`.<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime`, `DateTimeOffset`, lub `Time`. **Uwaga:** `startExpression` i `endExpression` muszą być tego samego typu. <br /><br /> **Wartość zwracana**<br /><br /> `Int32`.|  
|`DiffMinutes(startExpression,endExpression)`|Zwraca różnicę (w minutach) między `startExpression` i `endExpression`.<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime`, `DateTimeOffset`, lub `Time`. **Uwaga:** `startExpression` i `endExpression` muszą być tego samego typu. <br /><br /> **Wartość zwracana**<br /><br /> `Int32`.|  
|`DiffHours(startExpression,endExpression)`|Zwraca różnicę w godzinach między `startExpression` i `endExpression`.<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime`, `DateTimeOffset`, lub `Time`. **Uwaga:** `startExpression` i `endExpression` muszą być tego samego typu. <br /><br /> **Wartość zwracana**<br /><br /> `Int32`.|  
|`DiffDays(startExpression,endExpression)`|Zwraca różnicę, dni, między `startExpression` i `endExpression`.<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime` lub `DateTimeOffset`. **Uwaga:** `startExpression` i `endExpression` muszą być tego samego typu. <br /><br /> **Wartość zwracana**<br /><br /> `Int32`.|  
|`DiffMonths(startExpression,endExpression)`|Zwraca różnicę w miesiącach między `startExpression` i `endExpression`.<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime` lub `DateTimeOffset`. **Uwaga:** `startExpression` i `endExpression` muszą być tego samego typu. <br /><br /> **Wartość zwracana**<br /><br /> `Int32`.|  
|`DiffYears(startExpression,endExpression)`|Zwraca różnicę w latach między `startExpression` i `endExpression`.<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime` lub `DateTimeOffset`. **Uwaga:** `startExpression` i `endExpression` muszą być tego samego typu. <br /><br /> **Wartość zwracana**<br /><br /> `Int32`.|  
|`GetTotalOffsetMinutes(datetimeoffset)`|Zwraca liczbę minut, która `datetimeoffset` przesunięcia względem GMT. Zwykle jest to między +780 i-780 (+ lub - 13 godz.). **Uwaga:**  Ta funkcja jest obsługiwana tylko w programie SQL Server 2008. <br /><br /> **Argumenty**<br /><br /> A `DateTimeOffset`.<br /><br /> **Wartość zwracana**<br /><br /> `Int32`.|  
|`Hour(expression)`|Zwraca część dotyczącą godziny z `expression` jako `Int32` od 0 do 23.<br /><br /> **Argumenty**<br /><br /> A `DateTime, Time` i `DateTimeOffset`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns 22.`<br /><br /> `Hour(cast('22:35:5' as DateTime))`|  
|`Millisecond(expression)`|Zwraca część milisekund `expression` jako `Int32` od 0 do 999.<br /><br /> **Argumenty**<br /><br /> A `DateTime, Time` i `DateTimeOffset`.<br /><br /> **Wartość zwracana**<br /><br /> `Int32`.|  
|`Minute(expression)`|Zwraca część dotyczącą minut z `expression` jako `Int32` od 0 do 59.<br /><br /> **Argumenty**<br /><br /> A `DateTime, Time` lub `DateTimeOffset`.<br /><br /> **Wartość zwracana**<br /><br /> `Int32`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns 35`<br /><br /> `Minute(cast('22:35:5' as DateTime))`|  
|`Month(expression)`|Zwraca część dotyczącą miesiąca z `expression` jako `Int32` od 1 do 12.<br /><br /> **Argumenty**<br /><br /> A `DateTime` lub `DateTimeOffset`.<br /><br /> **Wartość zwracana**<br /><br /> `Int32`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns 3.`<br /><br /> `Month(cast('03/12/1998' as DateTime))`|  
|`Second(expression)`|Zwraca sekundy część `expression` jako `Int32` od 0 do 59.<br /><br /> **Argumenty**<br /><br /> A `DateTime, Time` i `DateTimeOffset`.<br /><br /> **Wartość zwracana**<br /><br /> `Int32`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns 5`<br /><br /> `Second(cast('22:35:5' as DateTime))`|  
|`TruncateTime(expression)`|Zwraca `expression`, za pomocą wartości czasu obcięte.<br /><br /> **Argumenty**<br /><br /> A `DateTime` lub `DateTimeOffset`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.|  
|`Year(expression)`|Zwraca część dotyczącą roku z `expression` jako `Int32` `YYYY`.<br /><br /> **Argumenty**<br /><br /> A `DateTime` i `DateTimeOffset`.<br /><br /> **Wartość zwracana**<br /><br /> `Int32`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns 1998.`<br /><br /> `Year(cast('03/12/1998' as DateTime))`|  
  
 Te funkcje zwrócą `null` Jeśli `null` danych wejściowych.  
  
 Równoważne funkcje są dostępne w Microsoft SQL klienta zarządzanego dostawcy. Aby uzyskać więcej informacji, zobacz [Klient SQL dla funkcji programu Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Zobacz także

- [Funkcje Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
