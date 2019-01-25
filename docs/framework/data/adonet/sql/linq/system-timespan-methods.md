---
title: System.TimeSpan Methods
ms.date: 03/30/2017
ms.assetid: 9333fee8-1454-4374-855b-8c14c002f48f
ms.openlocfilehash: a3f3c82f9f8db4b72588f165ed4d897b974eb076
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539912"
---
# <a name="systemtimespan-methods"></a>System.TimeSpan Methods
Element członkowski obsługę <xref:System.TimeSpan?displayProperty=nameWithType> zależy od wersji .NET Framework i programu Microsoft SQL Server, którego używasz.  
  
 Gdy metoda, operator lub właściwość nie jest obsługiwany; oznacza to, że LINQ to SQL nie może tłumaczyć elementu członkowskiego do wykonania w programie SQL Server. Nadal można użyć tych elementów członkowskich w kodzie. Muszą one jednak obliczane, przed zapytania jest tłumaczony języka Transact-SQL lub po wyniki zostały pobrane z bazy danych.  
  
## <a name="previous-limitations"></a>Ograniczenia dotyczące poprzedniego  
 Korzystając z programu LINQ to SQL z wersjami programu .NET Framework wcześniejszych niż .NET Framework 3.5 z dodatkiem SP1, nie można zamapować pola bazy danych programu SQL Server do <xref:System.TimeSpan?displayProperty=nameWithType>. Jednak operacje na <xref:System.TimeSpan> są obsługiwane, ponieważ <xref:System.TimeSpan> wartości mogą być zwracane przez <xref:System.DateTime> odejmowania lub wprowadzane do wyrażenia jako zmienną literału lub powiązanej.  
  
## <a name="supported-systemtimespan-member-support"></a>Obsługiwane obsługi elementu członkowskiego System.TimeSpan

 Następujące LINQ to SQL obsługiwanych metod, operatorów i właściwości są dostępne do użycia w Twojej zapytania LINQ to SQL. Po mapowane w modelu obiektu lub pliku mapowania zewnętrznych, LINQ to SQL pozwala wywołać wiele <xref:System.TimeSpan?displayProperty=nameWithType> członków wewnątrz Twojego zapytania LINQ to SQL.  
  
|Obsługiwane <xref:System.TimeSpan> metody|Obsługiwane <xref:System.TimeSpan> operatorów|Obsługiwane <xref:System.TimeSpan> właściwości|  
|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.TimeSpan.Compare%2A>|<xref:System.TimeSpan.op_Equality%2A>|<xref:System.TimeSpan.Days%2A>|  
|<xref:System.TimeSpan.CompareTo%28System.TimeSpan%29>|<xref:System.TimeSpan.op_GreaterThan%2A>|<xref:System.TimeSpan.Hours%2A>|  
|<xref:System.TimeSpan.Duration%2A>|<xref:System.TimeSpan.op_GreaterThanOrEqual%2A>|<xref:System.TimeSpan.MaxValue>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%2CSystem.TimeSpan%29>|<xref:System.TimeSpan.op_Inequality%2A>|<xref:System.TimeSpan.Milliseconds%2A>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%29>|<xref:System.TimeSpan.op_LessThan%2A>|<xref:System.TimeSpan.Minutes%2A>|  
||<xref:System.TimeSpan.op_LessThanOrEqual%2A>|<xref:System.TimeSpan.MinValue>|  
  
> [!NOTE]
>  Możliwość mapowania <xref:System.TimeSpan?displayProperty=nameWithType> SQL `TIME` kolumny za pomocą LINQ to SQL wymaga .NET Framework 3.5 SP1 i nowszych. SQL `TIME` — typ danych jest tylko dostępne w programie Microsoft SQL Server 2008 i nie tylko.  
  
### <a name="addition-and-subtraction"></a>Dodawanie i odejmowanie  
 Chociaż środowisko CLR <xref:System.TimeSpan?displayProperty=nameWithType> typ obsługuje dodawanie i odejmowanie, SQL `TIME` nie ma typu. W związku z tym Twoje zapytania LINQ to SQL będzie generować błędy, jeśli one próba Dodawanie i odejmowanie, gdy są mapowane do bazy danych SQL `TIME` typu. Możesz znaleźć inne zagadnienia dotyczące pracy z SQL typów daty i godziny w [mapowanie typu SQL CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
## <a name="see-also"></a>Zobacz także
- [Pojęcia dotyczące zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [Tworzenie modelu obiektu](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [Mapowania typów środowiska SQL-CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [Typy danych i funkcje](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
