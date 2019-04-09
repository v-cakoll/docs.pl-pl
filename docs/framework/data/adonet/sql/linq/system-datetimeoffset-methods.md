---
title: System.DateTimeOffset Methods
ms.date: 03/30/2017
ms.assetid: 25b3e5c0-7603-4a70-b3e5-2149e3da69a2
ms.openlocfilehash: 288a0d99feecdeccc0d215ec3c14ec31bb3ccb54
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59149724"
---
# <a name="systemdatetimeoffset-methods"></a>System.DateTimeOffset, metody
Gdy mapowane w modelu obiektu lub pliku mapowania zewnętrznych, LINQ to SQL pozwala wywoływać większość <xref:System.DateTimeOffset?displayProperty=nameWithType> metody, operatorów i właściwości z LINQ do zapytań SQL.  
  
 Jedyne metody, które nie są obsługiwane są te odziedziczone z <xref:System.Object?displayProperty=nameWithType> , nie mają sensu w kontekście LINQ do zapytań SQL, takich jak: `Finalize`, `GetHashCode`, `GetType`, i `MemberwiseClone`. Te metody nie są obsługiwane, ponieważ LINQ to SQL nie może ich tłumaczyć do wykonania w programie SQL Server.  
  
> [!NOTE]
>  Środowisko uruchomieniowe języka wspólnego (CLR) <xref:System.DateTimeOffset?displayProperty=nameWithType> struktury i możliwości w celu zamapowania go do bazy danych SQL `DATETIMEOFFSET` kolumny za pomocą LINQ to SQL, wymaga platformy .NET Framework 3.5 z dodatkiem SP1 lub nowszych. SQL `DATETIMEOFFSET` kolumny dostępną tylko w programie Microsoft SQL Server 2008 i nie tylko.  
  
## <a name="sqlmethods-date-and-time-methods"></a>SQLMethods daty i godziny metody  
 Oprócz metod oferowane przez <xref:System.DateTimeOffset> struktury, LINQ to SQL oferuje metody wymienione w poniższej tabeli z <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> klasy do pracy z datą i godziną.  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a>Zobacz także

- [Pojęcia dotyczące zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [Tworzenie modelu obiektu](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [Mapowania typów środowiska SQL-CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
