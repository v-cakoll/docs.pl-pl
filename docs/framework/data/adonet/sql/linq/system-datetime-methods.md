---
title: System.DateTime Methods
ms.date: 03/30/2017
ms.assetid: 4f80700c-e83f-4ab6-af0f-1c9a606e1133
ms.openlocfilehash: 85af6f252362b811356d68a3ae220df2bb813882
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59106330"
---
# <a name="systemdatetime-methods"></a>System.DateTime, metody
Następujące LINQ to SQL obsługiwanych metod, operatorów i właściwości są dostępne do użycia w składniku LINQ do zapytań SQL. Gdy metoda, operator lub właściwość nie jest obsługiwany, LINQ to SQL nie wykonuje translację elementu członkowskiego do wykonania w programie SQL Server. Może użyć tych elementów członkowskich w kodzie, jednak one muszą zostać ocenione przed zapytania jest tłumaczony języka Transact-SQL lub po wyniki zostały pobrane z bazy danych.  
  
## <a name="supported-systemdatetime-members"></a>Elementy członkowskie obsługiwanych System.DateTime  
 Gdy mapowane w modelu obiektu lub pliku mapowania zewnętrznych, LINQ to SQL pozwala wywoływać następujące <xref:System.DateTime?displayProperty=nameWithType> członków wewnątrz LINQ do zapytań SQL.  
  
|Obsługiwane <xref:System.DateTime> metody|Obsługiwane <xref:System.DateTime> operatorów|Obsługiwane <xref:System.DateTime> właściwości|  
|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Add%2A>|<xref:System.DateTime.op_Addition%2A>|<xref:System.DateTime.Date%2A>|  
|<xref:System.DateTime.AddDays%2A>|<xref:System.DateTime.op_Equality%2A>|<xref:System.DateTime.Day%2A>|  
|<xref:System.DateTime.AddHours%2A>|<xref:System.DateTime.op_GreaterThan%2A>|<xref:System.DateTime.DayOfWeek%2A>|  
|<xref:System.DateTime.AddMilliseconds%2A>|<xref:System.DateTime.op_GreaterThanOrEqual%2A>|<xref:System.DateTime.DayOfYear%2A>|  
|<xref:System.DateTime.AddMinutes%2A>|<xref:System.DateTime.op_Inequality%2A>|<xref:System.DateTime.Hour%2A>|  
|<xref:System.DateTime.AddMonths%2A>|<xref:System.DateTime.op_LessThan%2A>|<xref:System.DateTime.Millisecond%2A>|  
|<xref:System.DateTime.AddSeconds%2A>|<xref:System.DateTime.op_LessThanOrEqual%2A>|<xref:System.DateTime.Minute%2A>|  
|<xref:System.DateTime.AddTicks%2A>|<xref:System.DateTime.op_Subtraction%2A>|<xref:System.DateTime.Month%2A>|  
|<xref:System.DateTime.AddYears%2A>||<xref:System.DateTime.Now%2A>|  
|<xref:System.DateTime.Compare%2A>||<xref:System.DateTime.Second%2A>|  
|<xref:System.DateTime.CompareTo%28System.DateTime%29>||<xref:System.DateTime.TimeOfDay%2A>|  
|<xref:System.DateTime.Equals%28System.DateTime%29>||<xref:System.DateTime.Today%2A>|  
|||<xref:System.DateTime.Year%2A>|  
  
## <a name="members-not-supported-by-linq-to-sql"></a>Elementy członkowskie nie są obsługiwane w składniku LINQ to SQL  
 Następujące elementy członkowskie nie są obsługiwane wewnątrz LINQ do zapytań SQL.  
  
|||  
|-|-|  
|<xref:System.DateTime.IsDaylightSavingTime%2A>|<xref:System.DateTime.IsLeapYear%2A>|  
|<xref:System.DateTime.DaysInMonth%2A>|<xref:System.DateTime.ToBinary%2A>|  
|<xref:System.DateTime.ToFileTime%2A>|<xref:System.DateTime.ToFileTimeUtc%2A>|  
|<xref:System.DateTime.ToLongDateString%2A>|<xref:System.DateTime.ToLongTimeString%2A>|  
|<xref:System.DateTime.ToOADate%2A>|<xref:System.DateTime.ToShortDateString%2A>|  
|<xref:System.DateTime.ToShortTimeString%2A>|<xref:System.DateTime.ToUniversalTime%2A>|  
|<xref:System.DateTime.FromBinary%2A>|<xref:System.DateTime.UtcNow%2A>|  
|<xref:System.DateTime.FromFileTime%2A>|<xref:System.DateTime.FromFileTimeUtc%2A>|  
|<xref:System.DateTime.FromOADate%2A>|<xref:System.DateTime.GetDateTimeFormats%2A>|  
  
## <a name="method-translation-example"></a>Przykład tłumaczenie — metoda  
 Wszystkie metody w składniku LINQ to SQL są tłumaczone na instrukcji języka Transact-SQL, przed wysłaniem ich do programu SQL Server. Na przykład rozważmy następujący wzorzec.  
  
 `(dateTime1 – dateTime2).{Days, Hours, Milliseconds, Minutes, Months, Seconds, Years}`  
  
 Po rozpoznaniu go jest tłumaczony na bezpośrednie wywołanie do programu SQL Server `DATEDIFF` funkcji w następujący sposób:  
  
 `DATEDIFF({DatePart}, @dateTime1, @dateTime2)`  
  
## <a name="sqlmethods-date-and-time-methods"></a>SQLMethods daty i godziny metody  
 Oprócz metod oferowane przez <xref:System.DateTime> struktury, LINQ to SQL oferuje metody wymienione w poniższej tabeli z <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> klasy do pracy z datą i godziną.  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a>Zobacz także

- [Pojęcia dotyczące zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [Tworzenie modelu obiektu](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [Mapowania typów środowiska SQL-CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [Typy danych i funkcje](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
