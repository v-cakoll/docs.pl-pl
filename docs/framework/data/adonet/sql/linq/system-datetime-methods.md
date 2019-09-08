---
title: System.DateTime Methods
ms.date: 03/30/2017
ms.assetid: 4f80700c-e83f-4ab6-af0f-1c9a606e1133
ms.openlocfilehash: fba695975645ecb86a06b17f0664fdf37f8866a0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792418"
---
# <a name="systemdatetime-methods"></a>System.DateTime, metody
Poniższe LINQ to SQL-obsługiwane metody, operatory i właściwości są dostępne do użycia w LINQ to SQL zapytaniach. Gdy metoda, operator lub właściwość nie jest obsługiwana, LINQ to SQL nie może przetłumaczyć elementu członkowskiego na wykonanie na SQL Server. Możesz użyć tych członków w kodzie, ale muszą one być oceniane przed przetłumaczeniem zapytania na Transact-SQL lub po pobraniu wyników z bazy danych.  
  
## <a name="supported-systemdatetime-members"></a>Obsługiwane elementy członkowskie system. DateTime  
 Po zmapowaniu w modelu obiektów lub zewnętrznym pliku mapowania LINQ to SQL umożliwia wywoływanie następujących <xref:System.DateTime?displayProperty=nameWithType> elementów członkowskich wewnątrz zapytań LINQ to SQL.  
  
|Obsługiwane <xref:System.DateTime> metody|Obsługiwane <xref:System.DateTime> operatory|Obsługiwane <xref:System.DateTime> właściwości|  
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
  
## <a name="members-not-supported-by-linq-to-sql"></a>Elementy członkowskie nieobsługiwane przez LINQ to SQL  
 Następujące elementy członkowskie nie są obsługiwane wewnątrz zapytań LINQ to SQL.  
  
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
  
## <a name="method-translation-example"></a>Przykład tłumaczenia metody  
 Wszystkie metody obsługiwane przez LINQ to SQL są tłumaczone na Transact-SQL przed wysłaniem do SQL Server. Rozważmy na przykład następujący wzorzec.  
  
 `(dateTime1 – dateTime2).{Days, Hours, Milliseconds, Minutes, Months, Seconds, Years}`  
  
 Po rozpoznaniu są one tłumaczone na bezpośrednie wywołanie funkcji SQL Server `DATEDIFF` w następujący sposób:  
  
 `DATEDIFF({DatePart}, @dateTime1, @dateTime2)`  
  
## <a name="sqlmethods-date-and-time-methods"></a>Metody SqlMethods i Time  
 Oprócz metod oferowanych przez <xref:System.DateTime> strukturę LINQ to SQL oferują metody wymienione w poniższej tabeli <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> z klasy do pracy z datą i godziną.  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a>Zobacz także

- [Pojęcia dotyczące zapytań](query-concepts.md)
- [Tworzenie modelu obiektu](creating-the-object-model.md)
- [Mapowania typów środowiska SQL-CLR](sql-clr-type-mapping.md)
- [Typy danych i funkcje](data-types-and-functions.md)
