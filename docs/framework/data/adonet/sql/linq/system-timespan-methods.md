---
title: Obiekt System.TimeSpan metody
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9333fee8-1454-4374-855b-8c14c002f48f
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a32b57488b49e9fd2f4e6342391690b27d7ad825
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="systemtimespan-methods"></a>Obiekt System.TimeSpan metody
Obsługa elementu członkowskiego <xref:System.TimeSpan?displayProperty=nameWithType> zależy od wersji programu .NET Framework i program Microsoft SQL Server.  
  
 Gdy metoda, operator lub właściwość nie jest obsługiwany; oznacza to, że LINQ do SQL nie może dokonywać translacji elementu członkowskiego do wykonania na serwerze SQL. Można nadal używać tych elementów członkowskich w kodzie. Jednak ich musi przyjąć przed zapytania jest translacja języka Transact-SQL lub po wyniki zostały pobrane z bazy danych.  
  
## <a name="previous-limitations"></a>Ograniczenia poprzedniej  
 Podczas korzystania z LINQ do SQL z wersji programu .NET Framework, przed programu .NET Framework 3.5 z dodatkiem SP1, nie możesz mapować pola bazy danych programu SQL Server do <xref:System.TimeSpan?displayProperty=nameWithType>. Jednak operacje na <xref:System.TimeSpan> są obsługiwane, ponieważ <xref:System.TimeSpan> może zwracać wartości <xref:System.DateTime> odejmowania lub wprowadzane jako zmienną literału lub powiązane wyrażenia.  
  
## <a name="supported-systemtimespan-method-support"></a>Obsługiwana metoda System.TimeSpan pomocy technicznej  
 Następujące LINQ do operatorów, właściwości i metod obsługiwanych przez program SQL są dostępne do użycia w Twojej LINQ do zapytania SQL. Zmapowaniu w modelu obiektu lub plik mapowania zewnętrznych LINQ do SQL pozwala wywoływać wiele <xref:System.TimeSpan?displayProperty=nameWithType> członków wewnątrz programu LINQ do zapytania SQL.  
  
|Obsługiwane <xref:System.TimeSpan> metody|Obsługiwane <xref:System.TimeSpan> operatory|Obsługiwane <xref:System.TimeSpan> właściwości|  
|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.TimeSpan.Compare%2A>|<xref:System.TimeSpan.op_Equality%2A>|<xref:System.TimeSpan.Days%2A>|  
|<xref:System.TimeSpan.CompareTo%28System.TimeSpan%29>|<xref:System.TimeSpan.op_GreaterThan%2A>|<xref:System.TimeSpan.Hours%2A>|  
|<xref:System.TimeSpan.Duration%2A>|<xref:System.TimeSpan.op_GreaterThanOrEqual%2A>|<xref:System.TimeSpan.MaxValue>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%2CSystem.TimeSpan%29>|<xref:System.TimeSpan.op_Inequality%2A>|<xref:System.TimeSpan.Milliseconds%2A>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%29>|<xref:System.TimeSpan.op_LessThan%2A>|<xref:System.TimeSpan.Minutes%2A>|  
||<xref:System.TimeSpan.op_LessThanOrEqual%2A>|<!--zz <xref:System.TimeSpan.MinValue%2A>-->|  
  
> [!NOTE]
>  Możliwość mapowania <xref:System.TimeSpan?displayProperty=nameWithType> SQL `TIME` kolumny za pomocą LINQ do SQL wymaga platformy .NET Framework 3.5 SP1 i nowszych. SQL `TIME` — typ danych jest dostępna w programie Microsoft SQL Server 2008 i poza tylko.  
  
### <a name="addition-and-subtraction"></a>Dodawanie i odejmowanie  
 Mimo że środowisko CLR <xref:System.TimeSpan?displayProperty=nameWithType> typ obsługuje dodawanie i odejmowanie, SQL `TIME` nie ma typu. W związku z tym programu LINQ kwerendy SQL będzie generować błędy, jeśli próbują dodawania i odejmowania gdy są one mapowane na SQL `TIME` typu. Inne uwagi dotyczące pracy z typami daty i godziny w SQL można znaleźć [mapowanie typu środowiska CLR SQL](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia dotyczące zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [Tworzenie modelu obiektów](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 [Mapowanie typu środowiska CLR SQL](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)  
 [Typy danych i funkcje](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
