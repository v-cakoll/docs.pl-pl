---
title: Metody System.DateTimeOffset
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25b3e5c0-7603-4a70-b3e5-2149e3da69a2
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cbcd2af0b06eeb85c30c8a451877f5913e5d89e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="systemdatetimeoffset-methods"></a>Metody System.DateTimeOffset
Zmapowaniu w modelu obiektu lub plik mapowania zewnętrznych LINQ do SQL pozwala wywoływać większość <xref:System.DateTimeOffset?displayProperty=nameWithType> metody, Operatorzy i właściwości z Twojej LINQ do zapytania SQL.  
  
 Tylko metody nie jest obsługiwane są te dziedziczone z <xref:System.Object?displayProperty=nameWithType> które nie mają sensu w kontekście LINQ do zapytania SQL, takich jak: `Finalize`, `GetHashCode`, `GetType`, i `MemberwiseClone`. Te metody nie są obsługiwane, ponieważ LINQ do SQL nie może tłumaczyć je do wykonania na serwerze SQL.  
  
> [!NOTE]
>  Środowisko uruchomieniowe języka wspólnego (CLR) <xref:System.DateTimeOffset?displayProperty=nameWithType> struktury i możliwość mapowanie go SQL `DATETIMEOFFSET` kolumny za pomocą LINQ do SQL, wymaga platformy .NET Framework 3.5 z dodatkiem SP1 lub nowszych. SQL `DATETIMEOFFSET` kolumny jest dostępna w programie Microsoft SQL Server 2008 i poza tylko.  
  
## <a name="sqlmethods-date-and-time-methods"></a>SQLMethods Data i godzina metody  
 Oprócz metod oferowane przez <xref:System.DateTimeOffset> struktury LINQ do SQL oferuje metody wymienione w poniższej tabeli z <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> klasy do pracy z datą i godziną.  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia dotyczące zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [Tworzenie modelu obiektów](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 [Mapowanie typu środowiska CLR SQL](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
