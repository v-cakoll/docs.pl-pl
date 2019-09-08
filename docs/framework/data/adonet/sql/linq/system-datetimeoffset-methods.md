---
title: System.DateTimeOffset Methods
ms.date: 03/30/2017
ms.assetid: 25b3e5c0-7603-4a70-b3e5-2149e3da69a2
ms.openlocfilehash: 2e29cf02d4f7e8004782264bf940bb1faf393269
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781547"
---
# <a name="systemdatetimeoffset-methods"></a>System.DateTimeOffset, metody
Po zmapowaniu w modelu obiektów lub zewnętrznym pliku mapowania LINQ to SQL umożliwia wywoływanie większości <xref:System.DateTimeOffset?displayProperty=nameWithType> metod, operatorów i właściwości z zapytań LINQ to SQL.  
  
 <xref:System.Object?displayProperty=nameWithType> Jedyne metody nie są obsługiwane przez te, które nie mają sensu w kontekście zapytań LINQ to SQL, takich jak: `Finalize`, `GetHashCode`, `GetType`i `MemberwiseClone`. Te metody nie są obsługiwane, ponieważ LINQ to SQL nie można ich przetłumaczyć na SQL Server.  
  
> [!NOTE]
> Struktura środowiska uruchomieniowego języka wspólnego ( <xref:System.DateTimeOffset?displayProperty=nameWithType> CLR) i możliwość mapowania jej do kolumny SQL `DATETIMEOFFSET` z LINQ to SQL wymaga .NET Framework 3,5 z dodatkiem SP1 lub nowszych. Kolumna SQL `DATETIMEOFFSET` jest dostępna tylko w Microsoft SQL Server 2008 i poza nią.  
  
## <a name="sqlmethods-date-and-time-methods"></a>Metody SqlMethods i Time  
 Oprócz metod oferowanych przez <xref:System.DateTimeOffset> strukturę LINQ to SQL oferują metody wymienione w poniższej tabeli <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> z klasy do pracy z datą i godziną.  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a>Zobacz także

- [Pojęcia dotyczące zapytań](query-concepts.md)
- [Tworzenie modelu obiektu](creating-the-object-model.md)
- [Mapowania typów środowiska SQL-CLR](sql-clr-type-mapping.md)
